# GO-001 assessment — completed

## Outcome

Design and implementation loops completed with accepted MCP results. Design revision 2 was approved through the monitor; final human acceptance was approved through the monitor at 13:42:33Z. Factory records the execution as completed with no execution error. The independent reviewer reports no blocking implementation findings, all 10 acceptance criteria covered, and 14 tests / 21 subtests passing with race checks. The operator did not run product tests, oracle checks, or repairs. This is a workflow/evidence assessment, not independent product certification.

Execution: `b231d267-bfe4-4536-a5fa-918f8c8456c0`; context: `EXFRKGRN`.

## Usage

| Step | Uncached input | Cached input | Output | Total | Tool errors |
|---|---:|---:|---:|---:|---:|
| specification | 181,697 | 507,392 | 15,592 | 704,681 | 1 |
| architecture_review | 46,901 | 668,160 | 19,564 | 734,625 | 4 |
| build | 127,962 | 585,043 | 20,272 | 733,277 | 0 |
| code_review | 42,705 | 513,792 | 13,426 | 569,923 | 1 |

Total: **2,742,506 reported tokens** (399,265 uncached input, 2,274,387 cached input, 68,854 output). Reasoning is reported separately as 33,585 diagnostic tokens and is not added again. Cost is unknown; zero provider counters do not establish free usage.

Compared with the preceding concurrent GO-001 run: total reported tokens fell 45.2% (5,008,877 → 2,742,506); tool errors fell 27 → 6. Same case and models, changed runtime/skills/instructions; one run cannot establish a causal improvement or stable efficiency estimate. The previous run failed at acceptance; this run completed both human decisions and the final transition. One successful run does not establish durable recovery reliability.

Changed-line counts: production +59/−5; tests +321/−0. These are scope/accounting measures, not productivity or code-quality scores. spec.html is 18,323 bytes; plan.html is 17,350 bytes. Embedded styling contributes to these sizes; files remain substantial for this narrow case.

## Observed improvements

- Direct Pi tools were used successfully for participant discovery and messaging. No codemode JavaScript failures were observed.
- Content-only HTML helper was used. The model did not need to regenerate the shared stylesheet.
- Architecture reviewer caught header-absence ambiguity and loss of strict JSON validation in the plan. The author corrected both and published revision 2; reviewer verified resolutions using stable finding IDs.
- Concurrent peer delivery, idle waiting, corrected publications, and both result handoffs worked without operator routing or steering.
- No response-length continuations or provider failures were recorded in these four invocations.
- No direct oracle tool-path access was observed. This is an observation from logs, not proof of enforced isolation.

## Remaining issues for discussion

1. **Typed payload usability:** architect initially sent a publication without its required data part despite the example. Direct tool exposure removes JavaScript indirection but the broad envelope schema still permits invalid kind-specific content. Server rejected it; agent repaired the call.
2. **Publication readiness:** reviewers tried reading not-yet-created spec/plan/build evidence, causing three avoidable ENOENT errors. Reviewer startup still needs a clearer publication-first discipline.
3. **Scope and environment discipline:** builder searched the registry and `~/.factory` for a known helper, used generic `/tmp` filenames, and attempted `go run honnef.co` with errors suppressed. Host execution does not prevent downloads or access outside the assigned scope. Local preflight is not a sandbox.
4. **Trustworthy command evidence:** agents used shell pipelines, `|| true`, and suppressed errors. A successful pipeline exit can conceal a failing check. Reviewer independently ran plain test/race/vet commands, which mitigates product verification risk but does not repair the general evidence contract.
5. **Reviewer mutation and report precision:** reviewers ran `go mod tidy`, which can write module files. The code reviewer called `go vet` lint, and described `t.Helper` as a testify pattern despite no added dependencies. Reports need tighter separation of observed checks, tool names, and conclusions.
6. **Planning proportionality:** renderer reduced presentation work, but spec/plan content remains extensive. Measure content size and relevance across more task sizes before imposing a quota.

No framework/registry files were changed during this run. No model settings changed. Full raw JSON stream, reconstructed agent logs, tool errors, command evidence, and metrics are retained alongside the project.

## Finalization

Final acceptance: approved through the monitor at 2026-10-29T13:42:33Z. Execution state: completed. Design elapsed 368.6 seconds; implementation elapsed 278.6 seconds (parallel members are not summed). No operator product tests or oracle checks. Spec body: 1080 words; plan body: 1027 words, excluding shared shell and CSS.
