# SpecSprint

**Turns a product walkthrough, a Slack decision thread, and design context into a decision-ready PRD and reviewable implementation tickets.**

Track: Work & Productivity - OpenAI Build Week 2026

## Why it matters

Product requirements are often reconstructed manually from a Loom, a long Slack thread, Figma frames, and fragments of earlier docs. The result is a slow handoff and a PRD that loses decisions, open questions, or implementation details along the way.

SpecSprint fuses those sources into a team's PRD structure and voice, clearly traces sources, separates non-goals from open questions, and previews tickets before any external action is taken.

## Run locally

```bash
cd specclaw
pnpm start
# Open http://localhost:3003
```

The full local demo uses representative source data. Choose **Preview Linear tickets** to exercise the PRD-to-ticket handoff. No credentials are needed.

```bash
pnpm test
```

## GPT-5.6 integration

GPT-5.6 performs the central reasoning task: long-context fusion across a product-video transcript, Slack decisions and questions, Figma frame descriptions, and a past PRD's template and voice. Its structured result contains goals with measurable outcomes, non-goals, acceptance criteria, named open questions, rollout phases, and tickets that must be reviewed before creation.

The local demo is deterministic so judges can reliably test it without accounts. `src/services/prd-engine.js` defines the production GPT-5.6 context and response contract.

## Safe actions

- Ticket owners are suggestions, derived from source context and displayed for confirmation.
- Notion publishing and Linear ticket creation are always reviewable; the demo never silently posts externally.
- Connected source access must be scoped to the user’s workspace and OAuth permissions.
- The demo source pack is fictional and contains no customer data.

## Codex workflow

This project was built in the primary Codex Build Week session. Codex turned the implementation plan into a runnable decision-artifact workflow, authored the structured PRD and ticket contracts, added source traceability and review boundaries, then implemented the responsive UI, API, tests, and submission collateral. Add the primary `/feedback` Session ID here and to Devpost before submitting.

## Submission

See [SUBMISSION_CHECKLIST.md](SUBMISSION_CHECKLIST.md) for final Devpost requirements and a 3-minute demo outline.

## License

MIT. See [LICENSE](LICENSE).
