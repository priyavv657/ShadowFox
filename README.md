# Fielding Performance Analysis — T20 Match

This repository contains a fielding performance analysis template (Excel) for cricket, with sample data and formulas to compute metrics and a performance score.

## Contents
- `fielding_template_completed.xlsx` — Excel workbook with:
  - **RawEvents** sheet: where you record ball-by-ball fielding events (Pick, Throw, Runs, etc.)
  - **Summary** sheet: auto-calculates counts (Clean Picks, Catches, Run Outs, etc.) and computes **Performance Score (PS)** using weights
  - **Notes** sheet: listing valid values for Pick/Throw categories

## How to use
1. Open in **Excel** or upload to **Google Sheets** (formulas carry over).
2. In **RawEvents**, record each ball’s event for your chosen players.
3. Summary auto-updates per player with:
   - CP, GT, C, DC, ST, RO, MRO, DH, RS
   - PS = (CP×1) + (GT×1) + (C×3) + (DC×–3) + (ST×3) + (RO×3) + (MRO×–2) + (DH×2) + RS
4. Inspect **PS** values as measure of fielding contribution.

## Explanation of metrics & weights

| Metric                | Abbreviation | Weight | Notes |
|-----------------------|--------------|--------|-------|
| Clean Picks           | CP           | +1     | Clean pick-up of the ball |
| Good Throws           | GT           | +1     | Accurate, timely throw |
| Catches               | C            | +3     | Catch completed |
| Dropped Catches       | DC           | –3     | Drop the catch |
| Stumpings             | ST           | +3     | Completed stumping |
| Run Outs              | RO           | +3     | Run out effect (includes direct hit) |
| Missed Run Outs       | MRO          | –2     | Missed opportunity to kill run-out |
| Direct Hits           | DH           | +2     | Direct hit leading to run-out |
| Runs Saved / Conceded | RS           | + / –  | Add positive or negative runs effect |

Performance Score:
PS = (CP×1) + (GT×1) + (C×3) + (DC×–3) + (ST×3) + (RO×3) + (MRO×–2) + (DH×2) + RS