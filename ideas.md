# Flappy Bird Classic — Design Direction

## Three stylistic approaches

### Theme Name: Sunlit Handheld Arcade
Very brief intro: A warm, tactile arcade cabinet mood with paper grain, butter-yellow highlights, navy outlines, and crisp sprite-like geometry. The game should feel like a favorite cartridge discovered in a desk drawer.
Probability: 0.07

### Theme Name: Night Flight Observatory
Very brief intro: A midnight-blue sky with constellation-like particles, luminous pipes, and a tiny bird crossing a scientific instrument display. Calm, focused, and slightly mysterious.
Probability: 0.03

### Theme Name: Garden Parade
Very brief intro: A cheerful botanical side-scroll with leafy pipes, soft pastel clouds, and a storybook bird. Gentle and whimsical, with an emphasis on friendly motion and low-pressure play.
Probability: 0.05

## Chosen approach: Sunlit Handheld Arcade

### Design Movement
Neo-retro arcade illustration: 1980s home-console clarity interpreted with contemporary spacing, contrast, and interaction feedback.

### Core Principles
1. **Readable silhouettes first.** Every obstacle and action has a strong navy edge and simple geometric form so the game remains legible on a small mobile canvas.
2. **Warm tactile color.** The sky, ground, pipes, and bird use a compact palette that feels printed rather than digitally glossy.
3. **Motion with purpose.** The bird, ground, clouds, and score feedback all move at distinct speeds to communicate rhythm, not spectacle.
4. **Play immediately.** One tap or key press begins the run; screens explain only what is necessary and keep the focus on the next gap.

### Color Philosophy
The sky is a pale aqua field that makes the yellow bird and green pipes immediately legible. Butter yellow signals player agency, coral marks emphasis and danger, leaf green makes obstacles feel playful rather than hostile, and navy supplies the ink-like anchor that gives the whole scene its handheld-game identity.

### Layout Paradigm
The game is a single portrait cabinet floating inside a generous desktop stage. Within the canvas, the score sits on the open sky, while the start and game-over cards sit lower and slightly off-center so the playable field remains visible behind them.

### Signature Elements
1. A navy “ink” outline around the bird, pipes, cards, and score.
2. A moving ochre ground made from offset dashes and a dark lower rail.
3. Small pixel-cloud clusters and a soft sun disc that drift behind the action.

### Interaction Philosophy
Controls are direct and physical: every input immediately produces an upward impulse, a short audio chirp, and a tiny visual lift. Buttons feel like cabinet controls with a pressed state; there is no menu maze between the player and the first flap.

### Animation
The bird uses a three-phase wing cycle and rotates from a slight nose-up angle to a nose-down angle based on vertical velocity. Pipes travel at a steady speed. Clouds move at a slower parallax rate, while the ground moves faster than the clouds. Score changes briefly scale and tint the number. Reduced-motion preferences disable nonessential decorative drift while preserving playable motion.

### Typography System
Use a bold system monospace stack for arcade numerals and headings, paired with a clean system sans-serif stack for instructions. Headings are uppercase with generous tracking; labels are compact, high-contrast, and never smaller than 12px in the logical canvas coordinate system.

### Brand Essence
Flap City is a pocket arcade for players who want a one-button challenge with more personality than a score counter. Personality: **sunny, snappy, nostalgic**.

### Brand Voice
Headlines are short and confident. CTAs sound like a cabinet invitation rather than a marketing funnel. Microcopy is precise and playful.

Example lines: “Find the gap.” / “One more flight.”

### Wordmark & Logo
The mark is a circular badge containing an upward wing and a small star, with the wordmark rendered as chunky uppercase lettering beside it in the UI. The standalone canvas version recreates the badge procedurally so the file stays self-contained.

### Signature Brand Color
**Flap Yellow — #F8D34F**, the warm butter color shared by the bird, score accents, and cabinet-like interaction cues.

## Style Decisions

- Keep the deliverable a true single-file HTML artifact with inline CSS and JavaScript.
- Use procedural canvas shapes rather than external image, font, or audio dependencies.
- Preserve the generated art direction as a visual target, but draw the final gameplay scene in code for portability and crisp scaling.
