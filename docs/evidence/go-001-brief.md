# GO-001: Idempotent task creation

The existing Go HTTP service supports `POST /tasks` and `GET /tasks/{id}` using in-memory storage. Add optional `Idempotency-Key` support to `POST /tasks`.

- Without the header, preserve existing behavior: every valid POST creates a new task.
- With a nonempty key, the first valid POST creates one task and returns the usual `201` JSON response. Repeating the same key with the same request body must return the same status and response body without creating another task.
- Reusing a key with a different request body must return `409` with JSON `{"error":"idempotency key conflict"}` and must not create a task.
- An explicitly present but blank or whitespace-only key must return `400` and must not create a task. Trim surrounding whitespace from a nonblank key before comparing it. Compare request bodies as exact bytes; JSON documents with different byte representations are different requests.
- An invalid task request must not reserve its key. A later valid request may use that key.
- Concurrent requests using the same key and same body must create exactly one task and receive the same `201` response. Concurrent requests with that key and different bodies must yield one successful creation and conflicts for the other body.
- Keep the behavior in memory for the lifetime of one handler. No persistence or authentication is requested. Keep the existing endpoints, response shapes, and sequential task IDs.

Use the configured Go factory's normal specification, planning, approval, implementation, review, and acceptance flow. The assigned coder should add focused tests and run the relevant checks. The independent reviewer should verify the actual code and report limitations. Do not add dependencies or change the Go version unless the task requires it and the human approves.
