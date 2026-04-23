---
name: deep-research
description: Run source-backed multi-step research for market analysis, competitor analysis, decision support, trend scanning, and deep-dive reports. Use when the user asks for research, industry analysis, competitor analysis, report writing, or any answer that must go beyond a quick search and include verified sources, blind spots, and actionable conclusions.
license: MIT
metadata:
  openclaw:
    emoji: "🔬"
    category: "research"
    tags: ["research", "analysis", "multi-source", "decision-support"]
  hermes:
    tags: ["research", "analysis", "decision-support", "web", "reporting"]
    requires_toolsets: [web]
---

# Deep Research

Turn a vague research ask into a source-backed deliverable with clear conclusions, tradeoffs, and blind spots.

## Runtime Notes

- OpenClaw users can follow the named routing skills directly when those companion skills are installed.
- Hermes users can apply the same workflow by mapping `memory-search` to local memory or notes search, `multi-search-engine` to `web_search`, and `web-access` to `web_extract` or browser tools when interaction is required.

## Core Rules

1. Start with `memory-search` before doing any external research.
2. Confirm the research goal, budget, and output shape before collecting sources.
3. Check whether the task needs logged-in or private content before the main run starts.
4. Mix primary sources, practitioner/community sources, and comparative sources instead of relying on one search engine.
5. Mark every important claim as either fact, inference, or open question.
6. Always end with implications, risks, and next steps rather than raw notes.

## Research Controls

Choose these three controls up front:

### 1. Time Budget

- `S`: 5-10 minutes
- `M`: 15-30 minutes
- `L`: 30-60 minutes
- `XL`: 60+ minutes

### 2. Depth Tier

- `T1`: quick focus
- `T2`: structured comparison
- `T3`: decision memo / deep report

### 3. Deliverable Shape

- `briefing`: short answer with bullets and links
- `standard-report`: comparison, evidence, recommendation
- `deep-report`: executive summary, evidence map, implications, risks, next steps

If the user does not specify these controls, infer them and state the default you picked.

## Skill Routing

Use the minimum toolchain that can complete the job:

| Skill | Use for |
| --- | --- |
| `memory-search` | find prior internal context and avoid duplicate work |
| `multi-search-engine` | broad source discovery and quick source expansion |
| `web-access` | hard-to-fetch, JS-heavy, anti-bot, or login-gated pages |
| `video-to-summary` | video URLs that need transcription before analysis |
| `browser-troubleshooting` | browser/CDP failures blocking source access |

Use `web-access` only when plain fetch/search is not enough or the source is interaction-heavy.

## Preflight

Before the main run, confirm:

1. the decision or question this research will support
2. the likely geography and time window
3. whether cross-border access is required
4. whether private or logged-in sources are needed
5. whether the user wants a briefing, comparison, or deep report

If private or logged-in content is required, collect what is needed before the research run starts. Do not wait until you hit a login wall mid-task.

## Workflow

### 1. Reuse internal context

- run `memory-search`
- pull prior conclusions, entities, dates, and open threads
- record what still needs verification

### 2. Build the source list

- start with broad search terms
- expand into company docs, product docs, community discussion, and expert commentary
- prioritize first-party sources when facts or specs matter

### 3. Collect and verify

- read enough sources to meet the chosen budget and tier
- cross-check any important claim across more than one source when possible
- note source freshness and likely bias

### 4. Synthesize

- separate facts from interpretations
- identify tradeoffs, contradictions, and missing evidence
- extract the implications for the user's decision

### 5. Write the deliverable

At minimum, include:

- the answer or current conclusion
- the strongest supporting evidence
- what remains uncertain
- recommended next action

## Output Requirements

Use these minimum output shapes:

- `briefing`: answer first, then 3-7 evidence bullets, then risks/open questions
- `standard-report`: executive summary, comparison, recommendation, risks
- `deep-report`: executive summary, scope, evidence by theme, counterpoints, recommendation, blind spots, next steps

Every deliverable must expose at least one blind spot or uncertainty if the evidence is incomplete.

## Failure Handling

- If a source is blocked, retry with the next access tier instead of stopping.
- If logged-in content is required, pause and request the exact missing access.
- If source quality is weak, lower confidence and say why.
- If the task is too broad for the requested budget, narrow scope rather than pretending depth.

## References

Read these files only when needed:

- `references/report-levels.md`
  Use when you need the detailed budget/depth matrix and deliverable expectations.
- `references/source-routing.md`
  Use when routing URLs, deciding between search vs browser access, or checking login/private-source handling.
- `references/failure-handling.md`
  Use when the run is blocked, evidence conflicts, or the current plan is failing.
