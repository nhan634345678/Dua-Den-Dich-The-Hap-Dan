# Race to Victory

The complete static classroom game is in `artifacts/dua-den-dich/index.html`. Serve it directly; no framework build or database is needed. All 20 original questions, choices, answer keys and explanations remain unchanged. Formula presentation uses real subscripts and fractions.

## Answer and reward flow

A wrong answer shows the chosen option red and correct option green, without awarding points. A correct answer awards nothing automatically: it opens a choice between +1 điểm and Spin. The +1 branch opens a four-team score picker and requires an explicit recipient and confirmation. The Spin branch draws one persistent wheel outcome, then requires selecting its recipients and confirmation. Both branches advance after application. Wrong final answers finish via Tổng kết. No question countdowns exist.

Every wheel effect requires selecting a team. +1/+2/+3 adds points to the chosen recipient; reset sends the chosen team to zero; shield protects the chosen team; skip marks the chosen team's next turn. Swap requires two distinct teams and exchanges their scores/positions; a shield on either participant blocks it and is consumed once. Team Up requires two distinct teams and gives each +1. Nothing is applied to the answering team by default. All wheel and reward popup text is Vietnamese; the main game title remains English.

## Race and finish

Scores accumulate without a 20-point cap. During gameplay each runner's visual position is limited to space 19 and also kept a safe pixel distance before the finish line, including narrow screens. Neither manual +, correct answers, wheel bonuses, swapping nor reload can trigger an early result. Question 20 must be answered and its reward completed (or its wrong answer revealed) before results can open. On completion the highest score wins, with equal ranks and co-champions for ties.

Four horizontal lanes keep the live scores visible above the wheel/choice popup. + adds one manual point; each rewind icon can reverse only the most recent manual + for that lane. Global undo handles answer/reward changes. SVG runners animate their stride while moving. Results use a diamond cup, gold/silver/bronze podiums and restrained confetti.

## Recovery

`race-to-victory-wheel-v2` persists question/team, points, phase, wheel outcome, selections, shields and skipped turns. A pending feedback phase resumes at the reward choice; a pending spin resumes at the same outcome. Guards prevent double application. Existing v2 progress and earlier simple-game progress are retained. Previously saved early victories resume gameplay until question 20 completes. Undo is session-local. Replay resets the game.

## Verification

Browser checks cover both exclusive reward branches, all eight effects, explicit one/two-team selection, shields, skips, replay/reload, multiple manual additions beyond 20, actual runner geometry before the finish line, and final-question gating. Choice/point/wheel layouts keep the race visible at 1920×1080, 1366×768 and 390×844.
