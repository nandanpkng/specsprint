# SpecSprint

**Turns a product walkthrough, a Slack decision thread, and design context into a decision-ready PRD and reviewable implementation tickets.**

Track: Work & Productivity — OpenAI Build Week 2026

---

## Demo Video

- **Watch on YouTube:** https://youtu.be/jxFUUdI96kg

---

## The Problem

Product managers lose 4 to 8 hours per feature translating product walk-throughs (Looms), Slack decision threads, Figma mocks, and past documents into a team PRD. Traditional AI tools draft generic documents from a single prompt, losing key decisions, open questions, and acceptance criteria along the way. Breakdown into engineering tickets remains manual and error-prone.

---

## The Solution

SpecSprint ingests multi-source feature context and produces a complete, reviewable PRD and ticket set:
1. Fuses video transcripts (Loom), team discussion threads (Slack), and design links (Figma).
2. Formats the PRD into your team's specific document structure (Problem, Goals, Non-Goals, User Stories, Open Questions, Metrics).
3. Matches the product manager's writing voice using historical PRDs.
4. Automatically decomposes user stories into reviewable implementation tickets (Linear/Jira).

```text
Loom transcript + Slack thread + Figma link + Past PRD voice
  -> GPT-5.6 long-context fusion & structured PRD generation
  -> Human review & edit in single-page workspace
  -> Approved user stories pushed to Linear / Notion
```

---

## How Codex Was Used

SpecSprint was built 100% from scratch using OpenAI Codex as the primary software engineer.

### Codex Prompts Executed in Order:
1. `"Scaffold a Node.js Express web application for a product spec and ticket generation assistant."`
2. `"Create data ingestors for video transcriptions, Slack threads, Figma frames, and team PRD templates."`
3. `"Implement the GPT-5.6 long-context fusion engine that generates structured PRDs."`
4. `"Build a ticket decomposition algorithm that extracts acceptance criteria and assigns initial owners."`
5. `"Create a modern frontend workspace for reviewing PRDs, inspecting source citations, and previewing Linear tickets."`
6. `"Write automated unit tests for PRD generation and ticket decomposition."`

---

## GPT-5.6 Integration

GPT-5.6 handles the long-context multi-source reasoning:
- Fuses up to 50K tokens of heterogeneous transcripts, chat threads, and mock descriptions into one cohesive PRD.
- Matches team-specific voice and formatting guidelines ingested from past PRDs.
- Decomposes high-level requirements into atomic, reviewable user stories with explicit acceptance criteria.

### Code Snippet (`src/services/prd-engine.js`):
```javascript
const prd = await openai.chat.completions.create({
  model: "gpt-5.6",
  messages: [
    { role: "system", content: PRD_GENERATOR_SYSTEM_PROMPT },
    { role: "user", content: JSON.stringify({ transcript, slackThread, figmaContext, prdTemplate }) }
  ],
  response_format: { type: "json_object" }
});
```

---

## 9-Day Build Log

- **Day 1 (Jul 13):** Scaffolded Express server and multi-source data models (`src/services/demo-data.js`).
- **Day 2 (Jul 14):** Built transcript parser and Slack thread ingestion service.
- **Day 3 (Jul 15):** Implemented GPT-5.6 long-context fusion PRD generator (`src/services/prd-engine.js`).
- **Day 4 (Jul 16):** Added user story decomposition & Linear ticket preview engine (`src/services/ticket-engine.js`).
- **Day 5 (Jul 17):** Implemented source citation tracing and open questions extractor.
- **Day 6 (Jul 18):** Designed responsive frontend spec workspace (`src/public/index.html`, `src/public/app.js`).
- **Day 7 (Jul 19):** Created unit test suite (`tests/prd.test.js`) for deterministic local testing.
- **Day 8 (Jul 20):** Refined ticket preview modal, export triggers, and styling.
- **Day 9 (Jul 21):** Final validation, demo video scripting, and README documentation polish.

---

## Try It / Run Locally

### Prerequisites & Supported Platforms
- **Supported Platforms:** macOS, Linux, Windows
- **Runtime:** Node.js 20+
- **Credentials:** None required! The application includes a self-contained, offline-testable demo mode with pre-loaded Loom video transcripts, Slack threads, Figma mock links, and PRD templates.

### Quick Start

```bash
# 1. Clone repository
git clone https://github.com/nandanpkng/specsprint.git
cd specsprint

# 2. Start local server (zero npm dependencies required)
pnpm start   # or npm start / node src/server.js

# 3. Open in browser
# http://localhost:3003
```

### Self-Contained Judge Walkthrough
1. Navigate to `http://localhost:3003` in your web browser.
2. Review the multi-source input context (walkthrough transcript, Slack thread, Figma mocks).
3. Inspect the formatted PRD with problem statements, user stories, acceptance criteria, and open questions.
4. Click **Preview Linear tickets** to exercise the PRD-to-ticket decomposition and assignment workflow.

### Run Automated Tests
```bash
pnpm test   # or npm test / node --test
```

---

## Safety & Trust

- Generated tickets are previews; human review is required before publishing to Linear/Notion.
- Suggested owners are derived from source context and presented for confirmation.
- Demo source data is synthetic and contains no proprietary customer data.

---

## Prior vs. New Work

Built 100% from scratch during OpenAI Build Week 2026 (July 13–21, 2026) using OpenAI Codex and GPT-5.6. There is no pre-existing codebase or prior implementation.

---

## Connected Roadmap

1. Loom API & Whisper fallback transcription integration.
2. Slack OAuth & thread link expansion integration.
3. Notion API & Confluence publishing integration.
4. Linear & Jira REST API two-way synchronization.

---

## License

[MIT](LICENSE) © 2026 SpecSprint Team
