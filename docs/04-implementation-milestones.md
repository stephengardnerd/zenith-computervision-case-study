# Implementation Milestones

← [Back to README](../README.md)

---

## Milestone timeline

![Field mode flow](../images/field-mode-flow.svg)

---

## Build sequence

| Milestone | Proof point |
|---|---|
| Browser harness | Realtime voice, local camera preview, explicit frame send. |
| Cost guardrail | Continuous visual streaming replaced with bounded visual bursts. |
| HTTPS bridge | iPhone-compatible secure local testing path. |
| Native iOS shell | VisionZen installed and running on a physical iPhone. |
| Meta registration | App callback and developer-mode registration debugged. |
| Camera permission | Permission granted through Meta AI and reflected in app state. |
| Glasses session | Linked glasses detected and selected. |
| Glasses stream | Live frames received from the Ray-Ban camera. |
| Realtime voice | Z could hear and respond during API test mode. |
| Field mode | One-tap operational panel for the field workflow. |
| Pro manual lane | No-API frame package for ChatGPT Pro. |
| Perplexity grounding | Domain-aware grounding added for visual troubleshooting. |
| Native icon | App identity finished with a yin-yang and zenith-inspired icon. |

---

## What the sequence shows

This was an integration-heavy build. The final prototype matters, but the sequence matters too:

- isolate the core AI loop before wearable complexity
- keep a browser harness as a regression tool
- move slowly through native signing and device install
- expose device state in the UI while debugging
- add cost controls after observing real risk
- preserve a public artifact without leaking private code

