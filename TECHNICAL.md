# Technical Architecture — Zenith Computer Vision Case Study

> Public architecture overview for VisionZen. This document describes how the system fits together without exposing private implementation code, credentials, or proprietary SDK details.

---

## System architecture

![Architecture](images/architecture.svg)

At a high level, VisionZen has five layers:

| Layer | Responsibility |
|---|---|
| Wearable device | Meta Ray-Ban glasses provide camera context through the user's phone. |
| iPhone client | Handles registration, camera permission, local preview, field controls, and explicit user actions. |
| Hosted bridge | Provides contract discovery, policy flags, Realtime secret minting when authorized, and grounding endpoints. |
| Realtime voice loop | Runs low-latency voice interaction when API testing is explicitly enabled. |
| Grounding lane | Adds domain-aware, source-backed guidance for troubleshooting and how-to tasks. |

---

## Data-flow boundary

The important design decision is that **camera availability does not imply cloud upload**.

VisionZen separates:

- local preview and wearable session state
- explicit visual burst requests
- Realtime voice session state
- non-API manual handoff
- external grounding

This keeps the system useful in the field while preventing accidental long-running visual uploads.

---

## Realtime interaction model

The intended Realtime path is:

1. User explicitly authorizes an API test.
2. iPhone requests a short-lived Realtime client secret from the bridge.
3. Bridge refuses if API billing is disabled.
4. iPhone connects the voice session.
5. User speaks naturally to Z.
6. If the utterance requires visual context, the app sends the latest glasses frame as a bounded burst.
7. Z answers with voice and can be interrupted.

The product lesson: Realtime UX is not only model latency. It is also state, permissions, audio routing, interruption behavior, cost posture, and whether the user can tell what is happening.

---

## Wearable registration model

The iPhone app is responsible for the device-side workflow:

- register the app through the Meta AI app
- receive the callback
- observe registration state
- request camera permission
- discover linked glasses
- create a wearable session
- start the stream
- show whether frames are being received

The public case study does not publish SDK-specific implementation code. The value shown here is the integration approach, debugging sequence, and privacy/cost boundaries.

---

## Grounding model

Perplexity grounding is used for task context, not as the raw image interpreter.

| Input | Handler |
|---|---|
| Actual glasses frame | Realtime visual context |
| User task intent | Visual intent gate |
| Domain context and safety checks | Perplexity grounding |
| Final answer | Z combines observed visual evidence with grounded task guidance |

This split reduces overconfident visual guesses. For example, a blurry object should not be named as a specific tool unless the image evidence supports it.

---

## Cost and privacy controls

![Cost guardrails](images/cost-guardrails.svg)

The system was designed after a real cost lesson: always-on visual context can generate surprising API bills. The corrected architecture includes:

- API billing disabled by default
- bridge-level Realtime mint refusal when disabled
- explicit API-test mode
- idle-first camera preview
- bounded visual bursts
- manual ChatGPT Pro lane for no-API use
- visible billing state in the iPhone app

---

## Non-goals for this public repo

This repository intentionally does not include:

- iOS source code
- bridge source code
- API keys, client tokens, certificates, or environment files
- SDK callback implementation details
- glasses-captured media
- private prompts
- proprietary troubleshooting logs

That boundary is part of the engineering story. A strong public portfolio artifact can communicate architecture and judgment without leaking the build.

