# Source Routing

Use the cheapest reliable access path first, then escalate only when needed.

## Access Ladder

1. `memory-search`
2. `multi-search-engine`
3. direct fetch / normal webpage retrieval
4. `web-access`
5. `video-to-summary` for video URLs

## URL Routing

| Input type | Preferred path | Fallback |
| --- | --- | --- |
| normal webpage | direct fetch | `web-access` |
| GitHub repo / docs | direct fetch or docs pages | `web-access` |
| JS-heavy site | `web-access` | narrower source substitution |
| anti-bot page | `web-access` | alternative public source |
| video URL | `video-to-summary` | `web-access` page extraction |
| login-gated page | collect access first, then `web-access` | ask for alternate public source |

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
