# Task 3 — Fielding Performance Analysis (T20)

**Author:** Priyadharshini Vijayakumar 

**GitHub:** https://github.com/priyavv657/ShadowFox 

**Folder:** `task3_fielding`  

---

## Objective
This project provides a ball-by-ball data collection template and automated scoring matrix to evaluate fielding performance in a T20 innings. The deliverable is an Excel workbook (`fielding_template_completed.xlsx`) that:

- records every fielder action on a per-ball basis (RawEvents)
- summarizes per-player fielding metrics (Summary)
- computes a single **Performance Score (PS)** per player using a weighted formula to quantify impact

This work was implemented and validated by me (see **Work Log / Evidence** below).

---

## Files included
- `task3_fielding/fielding_template_completed.xlsx` — main workbook with three sheets:
  - **RawEvents** — row-per-ball manual entries (Match No., Innings, Player, BallCount, Pick, Throw, Runs, etc.)
  - **Summary** — computed player metrics and **Performance Score** (PS). Uses `COUNTIFS` / `SUMIFS` formulas referencing `RawEvents`.
  - **Notes** — allowed values and quick usage guide
- `task3_fielding/README.md` — this file (explanation, formulas, reproduction steps, evidence)

---

## Data schema (`RawEvents` sheet)
Each row = one fielder action for a particular ball. Columns:

| Column | Name | Example / Notes |
|---|---:|---|
| A | Match No. | `IPL2367` |
| B | Innings | `1` |
| C | Team | `Delhi Capitals` |
| D | Player Name | `Kuldeep Yadav` |
| E | BallCount | `0.1`, `0.2`, ... `1.6` |
| F | Position | `Point`, `Midwicket`, `Slip` |
| G | Short Description | short text describing the event |
| H | Pick | `Clean Pick`, `Good Throw`, `Catch`, `Drop Catch`, `Fumble`, `Bad Throw` |
| I | Throw | `Run Out`, `Missed Run Out`, `Stumping`, `Direct Hit`, `Missed Stumping`, `Good Throw`, `None` |
| J | Runs | numeric — **+** for runs saved, **−** for runs conceded |
| K | Overcount | numeric over number (1, 2, ...) |
| L | Venue | stadium name |

**Important rules & conventions**
- Use the exact text values in the Pick/Throw columns (case & spelling) — this ensures formulas count correctly.
- **One row per fielder action.** If more than one player acted on the same ball, add separate rows (same Match No./BallCount but different Player Name).
- If an action saves runs, put a positive number in `Runs`. If an action concedes runs (e.g., missed run-out cost 1 run), put a negative number.
- If multiple players jointly saved runs, assign RS to the decisive actor. If you split responsibility, record that split consistently and document it in the `Notes` sheet.

---

## Performance metric & formula

### Weights used
- **WCP (Clean Pick)** = +1  
- **WGT (Good Throw)** = +1  
- **WC (Catch)** = +3  
- **WDC (Dropped Catch)** = −3  
- **WST (Stumping)** = +3  
- **WRO (Run Out)** = +3  
- **WMRO (Missed Run Out)** = −2  
- **WDH (Direct Hit)** = +2  
- **RS (Runs Saved)** = + / − actual runs

### Performance Score (PS) formula
PS = (CP × 1) + (GT × 1) + (C × 3) + (DC × -3) + (ST × 3) + (RO × 3) + (MRO × -2) + (DH × 2) + RS
## Sample results (from included sample data)
> These results are from the example rows already included in the workbook (2 overs of sample events for three players).

| Player | CP | GT | C | DC | ST | RO | MRO | DH | RS | PS |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Kuldeep Yadav | 3 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 2 | **7** |
| Sameer Rizvi | 2 | 2 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | **1** |
| Faf du Plessis | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | −3 | **1** |

### Example manual PS calculation (Kuldeep Yadav)
- CP = 3 → 3 × 1 = 3  
- GT = 1 → 1 × 1 = 1  
- C = 0 → 0 × 3 = 0  
- DC = 0 → 0 × (−3) = 0  
- ST = 0 → 0 × 3 = 0  
- RO = 1 → 1 × 3 = 3  
- MRO = 1 → 1 × (−2) = −2  
- DH = 0 → 0 × 2 = 0  
- RS = 2  
Add: 3 + 1 + 0 + 0 + 0 + 3 − 2 + 0 + 2 = **7**

---

## How I collected the data (methodology)
1. Selected a single innings from a T20 match (chosen match and innings documented in `RawEvents` metadata).  
2. Played video / ball-by-ball feed. For each ball where one of my tracked players was involved, I:
   - Paused the video and recorded the row in `RawEvents` (match, ballcount, player, position, pick, throw, runs)
   - If more than one player acted, I added separate rows for each relevant player on the same BallCount (same ball, multiple rows).  
3. Followed attribution rules: decisive actor gets full RS; if ambiguous, split and noted split in `Notes`.
4. After entering data, validated counts in `Summary` and spot-checked PS computations by manual arithmetic.

---

## How to reproduce / run locally
1. Clone or pull the repository:
   ```bash
   git clone https://github.com/priyavv657/ShadowFox.git
   cd ShadowFox/task3_fielding
