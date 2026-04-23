# Failure Handling

Do not treat the first blocked source as the end of the run.

## Common Failure Types

| Failure | Response |
| --- | --- |
| timeout / transient network | retry, then switch source |
| 403 / anti-bot | move to `web-access` or an alternate source |
| JS verification / challenge HTML | stop using static fetch on that source and escalate to `web-access` CDP |
| login wall | stop and request the exact missing access |
| weak evidence | lower confidence and widen the source pool |
| conflicting sources | present the conflict explicitly and explain what is unresolved |
| overly broad scope | narrow the question to fit the budget |

## Static Fetch Failure Rule

Treat these as hard fetch failures, not "maybe one more retry":

- JavaScript verification pages
- anti-bot placeholder pages
- empty app shells with no usable content
- obviously partial HTML where the key data is missing

When one of those appears:

1. mark the static path as failed
2. escalate to `web-access` CDP if the source still matters
3. or replace the source with an HTML-friendly equivalent

Do not pretend the static response is evidence.

## What to Say When Confidence Drops

Be explicit:

- what is known
- what is likely but not proven
- what could not be verified
- what the next best verification step is

## Minimum Honest Output

If the run is blocked, still return:

1. what you were able to verify
2. what blocked completion
3. the best next action
4. the current confidence level
