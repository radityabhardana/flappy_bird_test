# Game Plan: Flappy Bird Classic

## Risk Tasks

### 1. Procedural pipe generation and collision
- **Why isolated:** Randomized vertical gaps and continuous scrolling can create unfair gaps or off-by-one collision errors when the canvas is scaled.
- **Approach:** Keep gameplay in a fixed logical coordinate system, generate pipes from a bounded deterministic-friendly random range, and use conservative AABB collision against the bird's inset hitbox and both pipe rectangles.
- **Verify:** Multiple runs produce varied but passable gaps; collision triggers precisely when the bird overlaps a pipe or the ground, including at mobile canvas scale.

### 2. Bird physics and rotation handoff
- **Why isolated:** Gravity, impulse, terminal velocity, and rotation must feel responsive while remaining stable under variable frame timing.
- **Approach:** Use delta-time clamped to a safe maximum, integrate velocity in logical units, cap fall speed, and map velocity to a bounded rotation with a short easing response.
- **Verify:** Space, click, and touch all create the same impulse; the bird tilts up after a flap, noses down during descent, and never tunnels through a boundary during a long frame.

### 3. Sprite-like wing animation and parallax
- **Why isolated:** High-frequency visual motion can stutter or visually detach from the gameplay loop if it is tied to input events rather than the animation clock.
- **Approach:** Drive wing phase, cloud drift, pipe scroll, and ground offset from the same requestAnimationFrame clock, with separate speeds for each layer.
- **Verify:** Wing motion remains continuous during idle and flight, clouds drift slower than pipes, and the ground visibly scrolls without gaps.

## Main Build

Build one self-contained `index.html` with an HTML5 canvas, responsive cabinet frame, inline CSS, and vanilla JavaScript. The game includes ready, playing, and game-over states; a local high score; keyboard, pointer, and touch controls; procedural Web Audio effects; and an optional `?demo` autopilot for visual verification.

- **Assets needed:** No external runtime assets. The generated visual reference, sprite study, and mark are recorded for direction; final sprites, clouds, pipes, ground, and badge are procedurally drawn in the canvas to preserve the standalone-file constraint.
- **Verify:**
  - Start screen, score HUD, game-over card, current score, and best score are readable at desktop and mobile dimensions.
  - LocalStorage restores the best score after reload.
  - Audio is unlocked after a user gesture and jump, score, and hit sounds are distinct.
  - Gameplay flow matches the PRD: start, flap, pass pipes for +1, collide, restart.
  - No visual clipping, missing assets, or third-party network dependencies.
  - No browser console errors during capture.
  - `?demo` renders a deterministic playable flight for screenshot verification.
