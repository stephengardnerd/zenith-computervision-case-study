# Realtime AI Systems — Skills Exercised

← [Back to README](../../README.md)

---

## Realtime is stateful product engineering

Realtime AI work includes model behavior, but the product surface depends on many non-model details:

- session creation
- socket readiness
- microphone capture
- assistant audio playback
- interruption
- transcript events
- turn detection
- visual context injection
- billing state

The prototype exposed and addressed these pieces one by one.

---

## Voice loop

The working test loop:

1. Mint a short-lived Realtime secret when API mode is authorized.
2. Connect the iPhone client.
3. Stream microphone audio.
4. Receive assistant audio chunks.
5. Play Z's response locally.
6. Allow the user to stop the assistant mid-response.

---

## Cost-aware Realtime design

Realtime systems can feel magical and still be economically unsafe. VisionZen therefore separates:

- Realtime voice tests
- visual frame bursts
- non-API manual handoff
- default API-off field mode

That separation is the product architecture.

