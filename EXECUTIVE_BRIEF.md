# Executive Brief

## What this is

This is a public proxy eval for legal AI systems operating at the action boundary.

It focuses on the moment a system is about to do something high-impact:

- accept a clause position
- route an agreement to signature
- mark a legal or compliance issue resolved
- clear compliance
- escalate or reroute a matter

The suite is based on workflow classes Luminance publicly markets. It is not an internal Luminance benchmark.

## What we measured

We ran the same harness in two modes:

- **baseline**
  identical workflow, prompts, playbooks, and tools, without VerifiedX
- **VerifiedX**
  same harness, with VerifiedX sitting at the action boundary

We measured:

- unjustified high-impact actions executed
- blocked unjustified actions
- false blocks on legitimate actions
- whether the underlying workflow still completed the real job

## Current result

Across 12 scenarios, run in both TypeScript and Python:

- baseline executed **18 unjustified high-impact actions**
- VerifiedX executed **0**
- VerifiedX false blocks in this suite: **0**
- surviving-goal completion improved from **41.7%** to **100%**

## Why that matters

The important point is not just "block more."

The system should:

- stop the wrong action
- tell the current node exactly why it was blocked
- in composed systems, return the receipt upstream to the orchestrator
- keep the overall workflow moving if the goal still legitimately survives

This suite shows both major real-world patterns:

- **blocked action, no retry**
  The action is wrong and should not be retried. The workflow continues through legal review, compliance review, redline, hold, or another lane.
- **blocked action, retryable after upstream change**
  The action is initially unjustified, but becomes legitimate after same-target upstream authority changes, such as GC exception approval or analyst false-positive clearance.

## Why this is credible

- same harness baseline vs protected
- dual-language lanes
- deterministic scenario truth
- raw artifacts published
- explicit methodology and limitations

## Recommended way to read it

- [README.md](README.md) for the one-minute view
- [RESULTS.md](RESULTS.md) for the scorecard
- [METHODOLOGY.md](METHODOLOGY.md) for how the suite was designed
- [artifacts/ts-full.json](artifacts/ts-full.json) and [artifacts/py-full.json](artifacts/py-full.json) for the raw evidence

## Suggested one-line takeaway

VerifiedX reduced executed unjustified legal workflow actions from 18 to 0 in this public proxy suite, while preserving legitimate workflow completion in 100% of the current protected runs.
