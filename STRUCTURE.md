# Structure: Flappy Bird Classic

The shipped artifact is intentionally a single standalone `index.html` file. The runtime uses one canvas and keeps the logical playfield at 432 × 768 units, then scales it to the available viewport with device-pixel-ratio awareness.

| Area | Ownership |
| --- | --- |
| `state` | Explicit `ready`, `playing`, and `over` state machine plus score persistence. |
| `bird` | Position, velocity, rotation, wing phase, and flap impulse. |
| `pipes` | Bounded procedural generation, horizontal scrolling, scoring, and AABB collision. |
| `render` | Canvas-only scene, UI cards, HUD, parallax layers, and sprite-like shapes. |
| `input` | Space/ArrowUp, pointer, and touch-safe pointer events mapped to one `flap()` action. |
| `audio` | Lazy Web Audio context with short oscillator-based jump, score, and hit effects. |
| `demo` | Optional deterministic autopilot activated by the `?demo` query flag. |

The React scaffold remains untouched as a host fallback, but the active entrypoint is the standalone inline document so the user can download and run it directly without a build step.
