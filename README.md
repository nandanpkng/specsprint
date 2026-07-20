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

## Installation & Supported Platforms

- **Supported Platforms:** macOS, Linux, Windows (Node.js 20+).
- **Installation:** Clone repo, run `pnpm install`, `pnpm start`.
- **Judge-Testable Path:** Run `pnpm start` and open `http://localhost:3003`. Select **Preview Linear tickets** to exercise the PRD-to-ticket handoff with pre-loaded representative source data.

## Codex Workflow Narrative

Built from scratch in the primary Codex Build Week session. Codex turned the architecture plan into a runnable decision-artifact workflow, authored the structured PRD and ticket contracts, added source traceability and review boundaries, and implemented the responsive UI, API, and automated test suite.

**Codex Session ID:** [Insert Session ID from primary build thread]

## Prior vs. New Work

Built from scratch during OpenAI Build Week 2026 using OpenAI Codex and GPT-5.6. There is no pre-existing codebase or prior implementation.

## License

MIT. See [LICENSE](LICENSE).
