# Failure Handling

Do not treat the first blocked source as the end of the run.

## Common Failure Types

| Failure | Response |
| --- | --- |
| timeout / transient network | retry, then switch source |
| 403 / anti-bot | move to `web-access` or an alternate source |
| login wall | stop and request the exact missing access |
| weak evidence | lower confidence and widen the source pool |
| conflicting sources | present the conflict explicitly and explain what is unresolved |
| overly broad scope | narrow the question to fit the budget |

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
