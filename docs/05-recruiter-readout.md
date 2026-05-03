# Recruiter Readout

← [Back to README](../README.md)

---

## How to read this project

This repository is a public artifact for a private implementation. It is not trying to prove that code exists by publishing it. It is trying to show the work that senior hiring teams usually care about:

- problem framing
- system boundaries
- technical tradeoffs
- privacy posture
- cost control
- integration sequencing
- product empathy
- real-device delivery

---

## Interview talking points

| Topic | What to discuss |
|---|---|
| Wearables | Device registration, permission state, camera session, field ergonomics. |
| Realtime AI | Voice loop, websocket/session state, interruption, latency, audio playback. |
| Computer vision | Explicit visual bursts, image uncertainty, visual + domain grounding split. |
| Cost control | Why always-on streaming is risky and how the product prevents it. |
| Mobile UX | Why the debug UI became Field Mode. |
| Security | Why public docs omit source code, keys, frames, and callback internals. |
| Product thinking | How a prototype became a field workflow with fallback lanes. |

---

## One-minute pitch

VisionZen is a wearable computer-vision assistant prototype that lets a user talk to an AI companion through Meta Ray-Ban glasses and an iPhone bridge. I built the system from browser proof to native iOS, navigated Meta wearable registration and camera permissions, streamed live glasses frames, connected a Realtime voice loop, and added cost/privacy guardrails after observing real billing risk. This public repo documents the architecture and product thinking without exposing private implementation code.

