# Race to Victory

## Source

The entire static game lives in `artifacts/dua-den-dich/index.html`. No server build or database is required. All 20 approved questions, options, answer keys and explanations remain unchanged. Formula display adds real subscripts and stacked fractions instead of raw underscore notation.

## Classroom flow

Start goes straight to question 1. Four horizontal 20-space race lanes have original SVG runners, finish lines and + controls. The teacher can select the answering team by its name. Default turns cycle 1 → 2 → 3 → 4. Wrong answers turn red, do not move any team and allow another attempt or Câu tiếp. A correct answer automatically awards one step, turns green and opens the wheel after a short visual feedback animation. No question countdowns or time limits exist. + is a manual additional one-step adjustment; Hoàn tác reverses mistakes. There is no minus control.

## Wheel

Eight equally likely sectors: +2, swap with a chosen opponent, skip the next team's turn, one-use shield, reset a chosen opponent to 0, +1, +3, and a gift of +1 to self and a chosen other team. Shield blocks one swap or reset and does not stack. Skip marks the immediate next team modulo four; the next-turn resolver consumes skip flags once. Target effects require an explicit target and cannot target self.

A result is drawn with browser cryptographic randomness and persisted before animation. Reload resumes the saved result without a second draw or point award. Effects are applied once; phase guards reject duplicate clicks. Applying an effect advances directly to the next question/team, retaining a short notice. Answer controls, team switching and manual scores lock while the wheel is pending. The wheel has keyboard focus trapping. Reduced motion still completes the transition.

## Victory

Reaching space 20 ends the game immediately. If all 20 questions finish first, the team with the highest score wins. Equal high scores produce co-champions; ranks and metal podiums use equal rank for equal scores. The victory screen has a custom faceted diamond cup, gold/silver/bronze podiums and restrained confetti. No prizes, timer setup or rule screens are present.

## Recovery

`race-to-victory-wheel-v2` stores scores, current question/team, wheel result/phase, shields and skip flags. Compatible saved progress from `race-to-victory-simple-v1` is migrated once when no v2 save exists. Pending feedback resumes at the wheel, and pending spin resumes at its recorded result. Session undo snapshots restore pre-action scores and phases; they are not persisted across reload. Replay resets all gameplay state. Fullscreen and optional A–D answer shortcuts remain.

## Design and validation

Projector targets: 1920×1080, 1600×900 and 1366×768. Mobile uses vertically stacked answers. Original trophy artwork and its canvas-design philosophy are in the local `design/` directory; the trophy SVG is embedded in the single HTML deployment.
