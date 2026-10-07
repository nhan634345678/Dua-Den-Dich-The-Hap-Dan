# Đua Đến Đích — Thế Hấp Dẫn

Classroom quiz race for four teams, optimized for a 16:9 projector.

## Source of truth

`artifacts/dua-den-dich/index.html` contains the complete HTML, CSS and JavaScript game. Serve this file directly; generated React components are unrelated to gameplay. Keep all 20 approved questions, answers and explanations unchanged.

## Gameplay architecture

CONFIG holds gameplay values: 20 spaces, 16 normal questions and 4 lightning questions, 30/60/90-second clocks, 15-second steal, card deck and special effects. S is the persisted state machine: question → steal (once if needed) → card → next question, or lightning → reveal → select correct teams → +2 → next question. Reaching 20 ends the race immediately; ties use a supplementary question.

Person-facing UI uses four persistent progress lanes, one current question and one primary action. Red move cards advance by face value; black move cards retreat by face value, clamped to 0–20. Red ace chooses a J/Q/K effect and target; black ace applies its effect to the drawing team (Q swaps with a random other team). Freeze skips one turn. Only the first global milestone crossing earns the pioneer badge.

## Persistence and undo

localStorage key: `dua-den-dich-vat-li11-v2`. Preserve compatibility with existing saved games. Persist card effect and random target so reload cannot redraw the effect. Undo snapshots restore the active screen and the preceding answer/card state. Team names and rewards persist between games.

## Keyboard controls

A–D select an answer, Enter/Space advances the current action, 1–4 picks effect targets or lightning teams, Z undoes, F toggles fullscreen, M toggles audio, Esc opens settings or closes a non-card modal. Inputs receive normal typing; repeated keydown events are ignored. An unresolved card modal must be applied or undone.

## Projector requirement

Target 1920×1080, 1600×900 and 1366×768 without vertical scroll. Keep important gameplay text large, timer out of the question, track at approximately 22% of height, and shortcuts inside help. Test long questions, revealed explanations and lightning states, not just the title.

## Local run

Any static HTTP server can serve the game. No database or React build is required for this source file.
