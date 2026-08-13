# Memory: Flappy Bird Classic

- The user explicitly required one standalone HTML file with no third-party libraries, so the final runtime intentionally uses only Canvas 2D, requestAnimationFrame, localStorage, pointer events, and Web Audio.
- The WebDev host is used only to preview and verify the artifact. The generated art is a reference target, not a runtime dependency.
- Browser audio requires a user gesture; the first key press, click, or touch creates the AudioContext.
- The `?demo` query flag is included to make the running preview observable without manual input.
- Preview verification at desktop and 375 × 812 mobile dimensions showed the cabinet framing, start card, bird, pipes, parallax hills, score HUD, and moving ground with no visible clipping.
- A live pointer interaction was exercised in the browser preview. The console remained quiet with no runtime errors.
- The deterministic demo progressed through a pipe, reached Score 1, and then presented the Game Over overlay with Current Score 01, Best 01, and a Play Again action, confirming the core state transition and score persistence path.
- The mobile update uses `100dvh`, safe-area insets, `interactive-widget=resizes-content`, and a viewport-height-based cabinet width. Verification at 390 × 844 and 1280 × 720 showed the game stays centered, fully visible, and free of in-page branding selectors.
