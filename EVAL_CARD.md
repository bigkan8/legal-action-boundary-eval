# Eval Card

## Name

**Legal Action Boundary Eval (LABE), Luminance proxy edition**

## Objective

Measure whether a legal AI system executes unjustified high-impact actions in negotiation, compliance, and composed legal workflows, while still completing the underlying business goal when the goal legitimately survives.

## Intended use

- public evidence for legal AI operators, governance leaders, product teams, and technical buyers
- baseline vs VerifiedX comparison on the same workflow harness
- regression suite for future action-boundary changes

## Non-goals

- overall legal answer quality
- clause extraction quality
- OCR / document ingestion quality
- Word plugin UX
- benchmark claims about internal Luminance systems

## Workflow families

- negotiation
- compliance
- composed supervisor/subagent workflows

## Scenario count

- 12 scenarios total
- 4 negotiation
- 4 compliance
- 4 composed

## Languages

- TypeScript
- Python

## Run configuration

| Field | Value |
| --- | --- |
| Run date | `2026-04-19` |
| Model | `gpt-5.4-mini` |
| VerifiedX API | `https://api.verifiedx.me` |
| TypeScript SDK | `@verifiedx-core/sdk@0.1.17` |
| Python SDK | `verifiedx==0.1.8` |

## Primary metrics

- unjustified high-impact actions attempted
- unjustified high-impact actions executed
- blocked unjustified actions
- false blocks on legitimate actions
- surviving-goal completion rate
- escalation/review rate
- same-action retry usage
- token, turn, tool-call, and latency overhead

## Current top-line result

Across both language lanes:

- baseline executed `18` unjustified actions
- VerifiedX executed `0`
- VerifiedX false blocks in this suite: `0`
- surviving-goal completion: `41.7% -> 100%`

## Threats to validity

- public proxy, not internal Luminance product code
- modest suite size; this is a v1 public release, not a final standard
- single model family on a single run date
- measures action control, not total legal workflow quality

## Distribution recommendation

Use alongside:

- [README.md](README.md) for the public landing page
- [METHODOLOGY.md](METHODOLOGY.md) for evaluator scrutiny
- [RESULTS.md](RESULTS.md) for scorecards and raw artifact links
- [EXECUTIVE_BRIEF.md](EXECUTIVE_BRIEF.md) for operator-facing sharing
