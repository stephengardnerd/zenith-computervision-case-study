# Computer Vision — Skills Exercised

← [Back to README](../../README.md)

---

## Vision context design

The key design choice was to treat visual context as an explicit event, not a continuous background stream. The user asks for help, the app captures the latest relevant frame, and the system sends a bounded visual burst.

This reduces:

- cost risk
- privacy risk
- context bloat
- stale visual evidence
- accidental uploads during idle time

---

## Uncertainty discipline

The assistant is expected to distinguish:

- what the image clearly shows
- what it might show
- what cannot be determined
- what safe next step the user can take

This matters because field assistance becomes dangerous if the model overclaims. "That might be a shutoff valve" is very different from "turn that valve now."

---

## Grounded visual troubleshooting

Visual perception is paired with domain grounding. For plumbing, homework, repair, translation, and how-to scenarios, VisionZen routes task context through Perplexity before answering.

The goal is not just "what is in the image?" The goal is "what should the user do next, safely and accurately?"

