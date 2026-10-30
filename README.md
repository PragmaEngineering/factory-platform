# Pragma platform site

A technical overview of Pragma's control plane, workflow definition, agent runtime, and operational interfaces.

`docs/index.html` and `docs/evaluation.html` are self-contained: HTML, CSS, JavaScript, and diagrams. No build, package installation, external fonts, or API connection is required. The home page links to the evaluation page; both use relative links for GitHub Pages repository subpaths. Configuration examples and the architecture inspector are interactive; the page does not connect to a running Pragma service.

## Preview

From this directory:

```sh
python3 -m http.server 8080 --directory docs
```

Open http://localhost:8080.

## GitHub Pages

The publishing source is `docs/`. No build or custom deployment workflow is needed.

1. Push this repository to GitHub, including `docs/.nojekyll`.
2. Open **Settings → Pages → Build and deployment**.
3. Set **Source** to **Deploy from a branch**.
4. Select **main** and **/docs**, then **Save**.
5. Use the published URL shown in Pages settings after deployment completes.

See [GitHub’s publishing-source instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

`docs/.nojekyll` disables Jekyll processing so the HTML and evidence files are served directly. Links are relative and navigation uses fragments, supporting both repository subpaths (such as `/platform/`) and custom domains. No backend, API credentials, package installation, or external assets are required. Repository Pages settings must be configured on GitHub; this checkout does not change them.

## Content boundaries

Keep technical claims aligned with the implementation in `../controls/`, especially:

- `docs/factory-json.md`: accepted configuration and concurrent loop rules.
- `docs/session-supervisor.md`: session delivery and recovery limits.
- `docs/execution-contract.md`: implemented behavior versus design targets.
- `comms.md`: thread tools, result acceptance, and messaging semantics.

Label proposed capabilities explicitly. Host execution is not sandboxing; durable engine state alone does not establish distributed control-plane guarantees.

## Evaluation page

`docs/evaluation.html` presents the frozen GO-001 run `GO-001-20261029-082749-concurrent`, the latest recorded run when the page was authored. It is not a live dashboard.

- Observed workflow and human decision timings.
- Filterable cached-input, uncached-input, and output token charts by agent step.
- Concrete design findings, reported product checks, tool errors, and operational limitations.
- Qualified comparison with the preceding concurrent run.
- Downloadable aggregates, the original brief, and original assessment under `docs/evidence/`.

Source: `../evals/factory-go/runs/GO-001-20261029-082749-concurrent/`. The embedded chart dataset matches `docs/evidence/go-001-summary.json`; update both together when intentionally publishing another frozen report. Keep failed comparisons and verification qualifications intact. Raw agent logs and private runtime paths are excluded. Product checks were reviewer-reported; the operator did not perform tests or oracle checks.

## Editorial style

Use the home page as an architecture reference and the evaluation page as a technical report. Prefer descriptive section titles, concrete interface and state semantics, measurements with defined denominators, source attribution, and explicit implementation limits. Avoid slogans, unsupported benefit claims, and promotional comparison language.
