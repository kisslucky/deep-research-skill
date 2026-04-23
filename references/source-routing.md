# Source Routing

Use the cheapest reliable access path first, then escalate only when needed.

## Access Ladder

1. `memory-search`
2. `multi-search-engine`
3. `linked-source-routing` when the user already supplied URLs
4. direct fetch / normal webpage retrieval
5. `web-access`
6. `video-to-summary` for video URLs

## Core Principle

Static fetch is a convenience layer, not a truth layer.

- Keep using direct fetch only if it returns the real page content.
- If it returns a JS verification page, anti-bot placeholder, empty shell, or obviously partial data, that path has already failed.
- When that happens, escalate to `web-access` CDP mode or use an alternate source family that exposes real HTML.

## URL Routing

| Input type | Preferred path | Fallback |
| --- | --- | --- |
| normal webpage | direct fetch | `web-access` |
| GitHub repo / docs | direct fetch or docs pages | `web-access` |
| supplied URL with unknown behavior | `linked-source-routing` | direct fetch or `web-access` |
| no-link research ask | `multi-search-engine` | `web-access` |
| JS-heavy site | `web-access` | narrower source substitution |
| anti-bot page | `web-access` | alternative public source |
| video URL | `video-to-summary` | `web-access` page extraction |
| login-gated page | collect access first, then `web-access` | ask for alternate public source |

## Search Engine Routing

Search result pages are not equal.

- Google search pages often return JS verification or anti-bot challenges to static fetch tools.
- If Google returns a challenge page, do not keep retrying static fetch.
- Prefer Bing, official site search, docs search, or HTML-friendly community sources for discovery.
- If the Google page itself is materially important, use `web-access` CDP mode.
- `old.reddit.com` is often a better HTML-first community source than the modern Reddit shell when static retrieval matters.

## Escalation Triggers

Move from fetch to `web-access` CDP immediately when any of these are true:

- the returned page asks for JavaScript execution before showing content
- the returned page is a challenge, captcha, or verification wall
- the visible browser page and fetched HTML clearly disagree
- the task needs login, scrolling, clicking, transcript expansion, or dynamic pagination
- important fields are known to be rendered client-side

## Private and Logged-In Sources

Check this before the main run starts:

- Does the task require personal accounts, private communities, or internal tools?
- Does the task need subscriber-only or member-only content?
- Does the task depend on a personal dashboard or CRM?

If yes, collect the access plan first:

- logged-in browser state
- screenshots or exports
- API keys or credentials
- a public substitute if access will not be granted

## Source Mix

Aim for a balanced mix:

- primary: official docs, company pages, filings, release notes
- comparative: competitors, alternative tools, adjacent products
- practitioner/community: Reddit, forums, product reviews, user writeups
- expert/context: analyst posts, domain experts, long-form commentary

Do not let a single source family dominate the conclusion unless the task is purely factual and first-party data is clearly authoritative.
