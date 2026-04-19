# Reproduce

## Prerequisites

- Node.js `18+`
- Python `3.10+`
- OpenAI API key
- VerifiedX API key

## Environment

Set these environment variables:

```powershell
$env:OPENAI_API_KEY="..."
$env:VERIFIEDX_API_KEY="..."
$env:OPENAI_MODEL="gpt-5.4-mini"
$env:OPENAI_TEMPERATURE="0"
$env:VERIFIEDX_BASE_URL="https://api.verifiedx.me"
```

## Install runtime dependencies

### TypeScript lane

```powershell
npm install --prefix evals/luminance_proxy/ts
```

### Python lane

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r evals/luminance_proxy/py/requirements.txt
```

## Run the full suite

### TypeScript

```powershell
node evals/luminance_proxy/ts/run_eval.mjs > evals/luminance_proxy/artifacts/ts-full.json
```

### Python

```powershell
python evals/luminance_proxy/py/run_eval.py > evals/luminance_proxy/artifacts/py-full.json
```

## Run a scenario subset

Both runners support the `LUMINANCE_EVAL_SCENARIOS` environment variable:

```powershell
$env:LUMINANCE_EVAL_SCENARIOS="comp_clear_real_sanctions_match,composed_negotiation_retryable_gc_exception"
node evals/luminance_proxy/ts/run_eval.mjs > evals/luminance_proxy/artifacts/ts-targeted.json
python evals/luminance_proxy/py/run_eval.py > evals/luminance_proxy/artifacts/py-targeted.json
Remove-Item Env:LUMINANCE_EVAL_SCENARIOS
```

## Regenerate the public report layer

```powershell
python evals/luminance_proxy/scripts/build_public_report.py
```

This regenerates:

- [RESULTS.md](RESULTS.md)
- [assets/summary.json](assets/summary.json)
- [assets/overview.svg](assets/overview.svg)
- [assets/track_breakdown.svg](assets/track_breakdown.svg)

## Compare your run with the current checked-in snapshot

- current TypeScript snapshot: [artifacts/ts-full.json](artifacts/ts-full.json)
- current Python snapshot: [artifacts/py-full.json](artifacts/py-full.json)
- current generated summary: [assets/summary.json](assets/summary.json)

## Notes

- The full suite makes real API calls and is materially more expensive than a targeted subset. Use `LUMINANCE_EVAL_SCENARIOS` for quick checks and rerun the full suite only when the harness or scenario truth changes.
- This suite intentionally evaluates the action boundary. If you change prompts, tools, or scenario truth, rerun both lanes and regenerate the report layer together.
