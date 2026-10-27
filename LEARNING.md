# Lesson 01 · Conversation evidence

AI-drafted task summary, not a transcript or grade. It may be public. Use actual
short quotes or labeled paraphrases, name any help supplied, and link actual
work. Leave missing contributions Pending. A learner can review, correct or
remove excerpts before publication; accuracy approval is not proof of learning.
Label role-play honestly rather than treating it as an actual learner response.

**Lesson:** STUDIO-001. **Available conversation context:** This coaching chat, 2026-10-27.

## Prediction

Before the plan, learner said: “It acts as a reverse proxy.”

## Check interpretation

Shown the actual `6 ÷ 0` API check (expected and actual HTTP 400), learner said:
“I see that the API is returning a 400 error for division by zero, which is the correct behavior. It means the server is handling invalid input properly.”

## Browser observation

For the classroom example, learner reported Browser result 42 (JavaScript,
calculated locally) and API result 42 (Python, verified by FastAPI).
After being asked to try `6 × 7` at https://373ai.bombayv.com, learner said:
“Results match.” Separate numeric results were not supplied for this observation.

## Keep decision

“Keep it since it's working fine,” following the matching-results observation.

## Review

Learner approved the corrected summary in this chat: “It's okay.”
Approval records accuracy review, not a grade or proof of understanding.

## AI work and next step

AI ran laptop setup, inspected the existing server, drafted the agreed scope,
and posted the reviewed [issue #1](https://github.com/BombayV/373_hosting/issues/1)
through the learner's browser. Learner approved launch and routing repairs.
AI's initial TLS-label fix was incomplete because Traefik uses only file routing;
AI added the approved calculator-only route, then identified the checker to
Cloudflare as `IS373-Studio/1.0`, preserving TLS and assertions.
Repeat verification passed; see [SPEC](SPEC.md) and
[sanitized runtime evidence](studio/evidence.json). No successful initial launch
report exists. Fast checks passed; full browser E2E/CI remains pending.
Next: review the diff and authorize commit/push/PR; full CI remains pending.
No grade or claim of independent understanding is assigned.
