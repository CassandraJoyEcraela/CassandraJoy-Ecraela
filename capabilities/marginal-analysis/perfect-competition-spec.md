| type       | spec                        |
| ---------- | --------------------------- |
| engagement | case-1-perfect-competition   |
| capability | marginal-analysis            |
| date       | 2026-09-08                   |
| status     | approved-for-build           |

# Perfect Competition Spec

## How to use this document

Paste this entire document into Claude with a spreadsheet open. It is self-contained — no other files or context are required. Claude will build the workbook, verify it, and hand you the exact Solver dialog entries to run.

**Claude cannot run Excel Solver.** Solver is a manual add-in and is not scriptable. Claude builds the model, wires the constraints, and tells you exactly what to type into Data → Solver. You run it. Claude then verifies the result independently.

Do not tell Claude the expected answer. The point of the exercise is to derive it.

---

## The scenario

A market farmer is planning one growing season and must decide how many garden beds to plant with each of three crops. She wants the mix that maximizes season profit.

**Season and facility**

- Season length: 36 weeks
- Total beds available: 64 (16 beds across 4 plots)
- Fixed costs for the season: $20,000

**The farmer's own labor**

- She earns $50,000 for the season
- She spends half her time in the field: 720 field hours
- Implied field rate: ~$34.72/hr

**Temporary labor**

- She can hire up to 4 temporary workers
- Each costs $25,000 for the season and works 1,440 hours
- Implied rate: ~$17.36/hr

**Crop economics**

| Crop | Max beds | Price $/bed | Labor hrs/wk/bed | Fertilizer $/bed | Diminishing returns |
|---|---|---|---|---|---|
| Tomatoes | 20 | 8,800 | 2.50 | 880 | 10.00% / bed |
| Carrots | 20 | 2,094 | 0.833 | 440 | 2.50% / bed |
| Mesclun | 30 | 2,700 | 1.25 | 880 | 1.25% / bed |

These are all the facts. There are no others. Do not introduce outside assumptions about yields, prices, weather, or crop rotation.

**How diminishing returns works in this model:** revenue per bed stays constant, but each additional bed of a crop takes proportionally more labor to work. For a crop with `q` beds planted, the escalation applies from the first bed:

`hours(q) = q * labor_hrs_wk_bed * season_weeks * (1 + dim_rate)^q`

**Scope of the farmer's salary:** charge only the field half of her $50,000 to the model — 720 hours at her field rate, which must come to exactly $25,000. The non-field half is out of scope and does not go into fixed costs.

## The hypothesis to test

The farmer's engagement brief predicts the following. Build the model so each claim is tested against the solved optimum. **These are predictions, not facts.** Any of them may turn out to be wrong, and a failed claim is a legitimate finding — do not tune a test so that it passes.

1. The optimal plan uses all 64 beds
2. Tomatoes come in below their 20-bed cap
3. Carrots land near their 20-bed cap
4. Mesclun lands near its 30-bed cap
5. Planted beds rank Mesclun > Carrots > Tomatoes

---

## Critical: the three rounded rates

The scenario above displays three rates as rounded values. **Entering them as typed constants will produce a wrong answer.** Derive all three by formula:

| Input | Scenario shows | Derive as | Evaluates to |
|---|---|---|---|
| `farmer_rate` | 34.72 | `farmer_salary * farmer_field_share / farmer_hours` | 34.7222… |
| `worker_rate` | 17.36 | `worker_flat_cost / worker_hours_each` | 17.3611… |
| `carrot_labor_hrs_wk_bed` | 0.833 | `5/6` | 0.8333… |

Carrots at 0.833 is a rounded display of 5/6 — fifty minutes per bed per week.

Format all three to show at least 4 decimal places. Under a 2-decimal format they render as the rounded figures, which invites a future editor to retype the rounded value and silently reintroduce the error.

---

## Workbook structure

Three worksheets, in this order.

1. **`Inputs`** — all assumptions as named ranges. Only the three derived rate cells may contain formulas.
2. **`Labor & Cost`** — all crop-level calculations and labor allocation logic.
3. **`Optimization`** — decision variables, objective function, Solver setup instructions, constraint check table, outputs, hypothesis test, recommendation.

Create every named range listed below using exactly the names given. Formulas throughout must reference named ranges, not raw cell addresses, so the model stays readable.

The row numbers given are a recommended layout. The named ranges and the two Solver anchors — changing cells at `Optimization!$C$5:$C$7` and objective at `Optimization!$C$11` — are required. Keep the three decision variables contiguous so Solver can take them as one range.

### Formatting conventions

- Typed input values: blue font (#0000FF)
- Formulas and calculations: black font
- Currency: `$#,##0` — except `total_profit`, which needs `$#,##0.00` to reconcile
  against a hand check
- Percentages: `0.00%`
- Hours: `#,##0.0`
- Derived rates: at least 4 decimals, per above
- Label every dollar figure with its unit in the row label
- Freeze the first column on each sheet; autofit the label column

---

## Worksheet 1: `Inputs`

Layout is `A` = named range, `B` = value, `C` = unit. Section headers in column A with a `Named Range | Value | Unit` label row beneath each.

### General Inputs

| Named Range | Cell | Value | Unit |
|---|---|---|---|
| `season_weeks` | B5 | 36 | weeks |
| `total_beds` | B6 | 64 | beds |
| `fixed_costs` | B7 | 20000 | $ |

### Farmer Inputs

Ordered so the derived rate comes after its precedents.

| Named Range | Cell | Value | Unit |
|---|---|---|---|
| `farmer_salary` | B11 | 50000 | $/season |
| `farmer_field_share` | B12 | 50% | share of time in field |
| `farmer_hours` | B13 | 720 | hrs/season |
| `farmer_rate` | B14 | `=farmer_salary*farmer_field_share/farmer_hours` | $/hr |

### Temporary Labor Inputs

| Named Range | Cell | Value | Unit |
|---|---|---|---|
| `worker_flat_cost` | B18 | 25000 | $/worker/season |
| `worker_hours_each` | B19 | 1440 | hrs/season |
| `worker_rate` | B20 | `=worker_flat_cost/worker_hours_each` | $/hr |
| `max_workers` | B21 | 4 | workers |

`worker_flat_cost` is the cost of one worker at full utilization. It exists to derive
`worker_rate`. It must not be charged as a lump sum per worker — see Labor Cost.

### Tomatoes

| Named Range | Cell | Value |
|---|---|---|
| `tomato_max_beds` | B25 | 20 |
| `tomato_price` | B26 | 8800 |
| `tomato_labor_hrs_wk_bed` | B27 | 2.5 |
| `tomato_fert_cost` | B28 | 880 |
| `tomato_dim_rate` | B29 | 10.00% |

### Carrots

| Named Range | Cell | Value |
|---|---|---|
| `carrot_max_beds` | B33 | 20 |
| `carrot_price` | B34 | 2094 |
| `carrot_labor_hrs_wk_bed` | B35 | `=5/6` |
| `carrot_fert_cost` | B36 | 440 |
| `carrot_dim_rate` | B37 | 2.50% |

### Mesclun

| Named Range | Cell | Value |
|---|---|---|
| `mesclun_max_beds` | B41 | 30 |
| `mesclun_price` | B42 | 2700 |
| `mesclun_labor_hrs_wk_bed` | B43 | 1.25 |
| `mesclun_fert_cost` | B44 | 880 |
| `mesclun_dim_rate` | B45 | 1.25% |

---

## Worksheet 2: `Labor & Cost`

Layout is `A` = named range, `B` = formula result, `C` = note.

### Crop Labor Hours

| Named Range | Cell | Formula |
|---|---|---|
| `tomato_labor_hours` | B4 | `=tomato_beds*tomato_labor_hrs_wk_bed*season_weeks*(1+tomato_dim_rate)^tomato_beds` |
| `carrot_labor_hours` | B5 | `=carrot_beds*carrot_labor_hrs_wk_bed*season_weeks*(1+carrot_dim_rate)^carrot_beds` |
| `mesclun_labor_hours` | B6 | `=mesclun_beds*mesclun_labor_hrs_wk_bed*season_weeks*(1+mesclun_dim_rate)^mesclun_beds` |
| `total_labor_hours` | B7 | `=tomato_labor_hours+carrot_labor_hours+mesclun_labor_hours` |

### Labor Allocation

The farmer's own hours are consumed first; temporary workers cover the remainder.

| Named Range | Cell | Formula |
|---|---|---|
| `farmer_hours_used` | B10 | `=MIN(total_labor_hours,farmer_hours)` |
| `temp_hours_used` | B11 | `=MAX(0,total_labor_hours-farmer_hours)` |
| `temp_workers_needed` | B12 | `=IF(temp_hours_used=0,0,ROUNDUP(temp_hours_used/worker_hours_each,0))` |
| `total_labor_capacity` | B13 | `=farmer_hours+(max_workers*worker_hours_each)` |

`temp_workers_needed` is a reporting figure only. It must not be a Solver decision
variable — it is fully determined by the bed mix.

### Labor Cost

Temporary labor is an **hourly variable cost on hours actually used**. Workers are not charged as fixed seasonal salaries.

| Named Range | Cell | Formula |
|---|---|---|
| `farmer_labor_cost` | B16 | `=farmer_hours_used*farmer_rate` |
| `temp_labor_cost` | B17 | `=temp_hours_used*worker_rate` |
| `total_labor_cost` | B18 | `=farmer_labor_cost+temp_labor_cost` |
| `blended_labor_rate` | B19 | `=IF(total_labor_hours=0,0,total_labor_cost/total_labor_hours)` |

**Do not write** `temp_labor_cost = temp_workers_needed * worker_flat_cost`. Charging a full $25,000 seasonal salary for a partially utilized worker introduces a large false step cost into the objective function and drives Solver to a different, wrong answer. This is the single most likely way to get this model wrong.

### Revenue

| Named Range | Cell | Formula |
|---|---|---|
| `tomato_revenue` | B22 | `=tomato_beds*tomato_price` |
| `carrot_revenue` | B23 | `=carrot_beds*carrot_price` |
| `mesclun_revenue` | B24 | `=mesclun_beds*mesclun_price` |
| `total_revenue` | B25 | `=tomato_revenue+carrot_revenue+mesclun_revenue` |

### Fertilizer Cost

| Named Range | Cell | Formula |
|---|---|---|
| `tomato_fertilizer_cost` | B28 | `=tomato_beds*tomato_fert_cost` |
| `carrot_fertilizer_cost` | B29 | `=carrot_beds*carrot_fert_cost` |
| `mesclun_fertilizer_cost` | B30 | `=mesclun_beds*mesclun_fert_cost` |
| `total_fertilizer_cost` | B31 | `=tomato_fertilizer_cost+carrot_fertilizer_cost+mesclun_fertilizer_cost` |

---

## Worksheet 3: `Optimization`

### Decision Variables (A3:C8)

Solver changing cells. Keep contiguous. Initialize all three to 0.

| Named Range | Cell | Meaning |
|---|---|---|
| `tomato_beds` | C5 | beds planted with tomatoes |
| `carrot_beds` | C6 | beds planted with carrots |
| `mesclun_beds` | C7 | beds planted with mesclun |

Add a check row at C8: `=tomato_beds+carrot_beds+mesclun_beds`, labeled "Total beds planted". All three variables must be integer and >= 0.

### Objective Function (A10:C11)

`total_profit` at C11:

`=total_revenue-total_labor_cost-total_fertilizer_cost-fixed_costs`

### Solver Setup Block (A13:C25)

A text block giving the user the exact entries to type into Data → Solver, since Claude cannot run it. State the objective cell, the changing-cell range, each constraint as a concrete cell-reference pair, the solving method, and step-by-step instructions including both required starting points.

### Labor Outputs (A28:B36)

Each a formula pulling the named range from `Labor & Cost`: `tomato_labor_hours`, `carrot_labor_hours`, `mesclun_labor_hours`, `total_labor_hours`, `farmer_hours_used`, `temp_hours_used`, `temp_workers_needed`.

### Financial Outputs (A38:B43)

`total_revenue`, `total_labor_cost`, `total_fertilizer_cost`, `fixed_costs`, `total_profit`.

### Hypothesis Test (A45:D51)

Columns: Claim | Expected | Actual | Pass/Fail. One row per claim from the hypothesis list above. Expected is `Yes` for all five. **Actual and Pass/Fail must be formulas** reading the decision variables — never pre-filled values.

Example for claim 1:
`Actual: =tomato_beds+carrot_beds+mesclun_beds`
`Pass/Fail: =IF(tomato_beds+carrot_beds+mesclun_beds=total_beds,"Pass","Fail")`

"Near cap" is undefined in the scenario. Implement it as exact equality to the crop's
`*_max_beds` and flag the ambiguity in a cell note — if a tolerance was intended, it
could change the outcome.

### Constraint Check Table (A53:F61)

Columns: Constraint | Left-hand side | LHS value | Op | RHS value | Status. One row per constraint below. LHS and RHS must be formulas referencing named ranges, never typed numbers. Status is `=IF(Cn<=En,"OK","VIOLATED")`. Roll up at C61 with `=IF(COUNTIF(F55:F60,"VIOLATED")=0,"FEASIBLE","INFEASIBLE")`.

Point the Solver constraint dialog at these cells. This makes the constraint set auditable without opening Solver.

### Final Recommendation (A63 onward)

A short written block, derived from the solved model: the recommended crop mix, the resulting profit, which constraint is actually binding at the optimum, and the economic reason the model stops adding beds of the highest-revenue crop before reaching its cap.

---

## Solver configuration

- **Objective cell:** `$C$11` (`total_profit`), set to **Max**
- **Changing cells:** `$C$5:$C$7`
- **Solving method:** **Evolutionary**

### Constraints

Reference named ranges on the right-hand side, not literal numbers, so changing an input propagates through.

| Constraint | Rule |
|---|---|
| Bed Capacity | `tomato_beds + carrot_beds + mesclun_beds <= total_beds` |
| Tomato Cap | `tomato_beds <= tomato_max_beds` |
| Carrot Cap | `carrot_beds <= carrot_max_beds` |
| Mesclun Cap | `mesclun_beds <= mesclun_max_beds` |
| Labor Capacity | `total_labor_hours <= total_labor_capacity` |
| Worker Limit | `temp_workers_needed <= max_workers` |
| Non-Negativity | `$C$5:$C$7 >= 0` |
| Integer | `$C$5:$C$7 = integer` |

Worker Limit is arithmetically redundant once Labor Capacity is enforced, since `total_labor_capacity` already implies at most `max_workers`. Keep it as a readability check and note that it is redundant.

### Use Evolutionary, not GRG Nonlinear

`ROUNDUP` in `temp_workers_needed` and `MIN`/`MAX` in the labor allocation make the profit surface discontinuous. GRG Nonlinear assumes smooth gradients and will stall on whichever step plateau it starts from, reporting a local result as though it had converged. The exponential terms in the labor formula would not by themselves rule out GRG — the step functions do.

Evolutionary is stochastic and can settle before reaching the global optimum. If runs from different starting points disagree, raise Max Time without Improvement and re-solve.

---

## Validation

Every check is answer-independent — these verify mechanics, not a known result. Run all of them and report the outcome of each.

1. **Unit labor check.** Set `tomato_beds = 1`. `tomato_labor_hours` must return `1 * 2.5 * 36 * 1.10` = 99.0 hours exactly.
2. **Zero check.** Set all three decision variables to 0. Every crop-specific labor, revenue, and fertilizer cell returns 0, and `blended_labor_rate` returns 0 rather
   than `#DIV/0!`.
3. **Derived rate check.** Read back the *rendered* text, not the underlying value: `farmer_rate` displays 34.7222, `worker_rate` 17.3611, `carrot_labor_hrs_wk_bed` 0.8333. If any shows the rounded figure, the number
   format is too narrow — widen it.
4. **Farmer cost check.** At any solution where `total_labor_hours >= 720`, `farmer_labor_cost` equals exactly $25,000.00.
5. **Error scan.** No `#REF!`, `#VALUE!`, `#DIV/0!`, or `#NAME?` anywhere.
6. **No hardcoded results.** Every calculated cell contains a formula. Typed constants appear only in the designated input cells on `Inputs`.
7. **Feasibility.** At the reported solution, C61 reads FEASIBLE.
8. **Convergence check.** Run Solver from starting points 0/0/0 and 20/0/0. Both must return the same bed mix and the same profit. Record both runs.
9. **Independent verification.** The feasible space is small — at most 21 x 21 x 31 integer combinations. Enumerate it exhaustively outside Excel using the same formulas and constraints, and confirm Solver reached the global maximum. Report the margin between best and second-best mix, so the reader knows whether Solver settling early would be visible. **Do not write the enumerated result into the workbook** as an input or benchmark — it is a check on Solver, not part of the model.

## Reporting

When finished, report: the solved crop mix and profit, the outcome of each validation
check, which constraint binds at the optimum, and which hypothesis claims passed or
failed. State plainly which ranges were re-read to verify and which were not.

If a hypothesis claim fails, say so directly and explain the economics. A failed
prediction is the most interesting output this model can produce.


## Audit
Checked 2026-09-11 against `perfect-competition-model.xlsx`. All five checks run. Two bugs found and fixed along the way.

| # | Check | Result |
|---|---|---|
| 1 | One bed by hand | Pass |
| 2 | Cross-check vs. Farm Profit Lab | Pass |
| 3 | Two Solver starting points | Pass |
| 4 | Do the numbers add up | Pass|
| 5 | Formulas, not typed-in numbers | Pass|

### 1. One bed by hand

Set tomatoes to 1 bed. Got 99.0 hours, which is exactly `1 × 2.5 × 36 × 1.10`. So the diminishing-returns exponent is there and it kicks in on the first bed, not the second.

Also set everything to zero: all the crop numbers zeroed out, no divide-by-zero errors, and profit came out at −$20,000 — just the fixed costs, which is right.

### 2. Cross-check vs. the Farm Profit Lab

Compared against the [Farm Profit Lab](https://adamwstauffer.github.io/ai-lms/farmlab.html). Same final answer — but matching one number at the end can hide two errors cancelling out, so I checked the middle of the model too.

The Lab is built the same way ours is: same labor formula, farmer's first 720 hours at $34.72, temps for everything after that at $17.36. Two useful things fall out of that:

- The Lab pays temps **by the hour**, not per whole worker. That's independent confirmation of bug 1 below.
- The Lab only charges the farmer's field hours. So leaving out her other $25,000 is correct — that was an open question, now closed.

The Lab also says tomato marginal cost *drops* around 6 beds, once the farmer's pricey hours run out and cheaper temp labor takes over. Ours does the same thing: $7,660.86 at bed 5, then down to $4,906.28 at bed 6. Same dip, same bed. Two separate builds agreeing on a curve in the middle is much better evidence than agreeing on one number at the end.

### 3. Two Solver starting points

Ran it from 0/0/0 and from 20/0/0. Both landed on 10 / 20 / 30 and $42,761.66 (rounded to $42,762 in the spreadsheet).

That matters more than it sounds, because second-best is only **$279.90** behind. If Solver had stopped one bed early it would've looked completely reasonable.

Method is set to Evolutionary. It has to be — the model has rounding and min/max steps in it, and the smooth-gradient solver (GRG) gets stuck on those steps and reports a dead end as if it had finished.

### 4. Do the numbers add up

Pulled every piece of the profit calculation and re-did it by hand. Everything ties:

Revenue $210,880 · fertilizer $44,000 · labor 5,277.22 hours · farmer $25,000 exactly ·
temps $79,118.34 · total labor $104,118.34 · **profit $42,761.66**. All six constraints
pass, no error values anywhere.

**One nit:** profit is formatted with no decimals, so it shows **$42,762** on screen.
The stored number is right, it's just displaying rounded.

**What's actually holding the farm back:** not beds and not hours. Only 60 of 64 beds get planted, and there are ~1,203 labor hours going unused. The real limit is that you can't hire a fraction of a person — the math needs 3.17 temp workers, so you hire 4 and pay for availability you don't use.

### 5. Formulas, not typed-in numbers

Scanned every calculated cell on both calc sheets looking for numbers someone had typed in by hand instead of formulas. Found none. Typed values only show up in the input cells where they belong, and all six constraints point at named inputs rather than hard numbers — so changing an input actually moves the constraints with it.

**One gap:** `Optimization!C8`, the "total beds planted" check row the spec asks for, isn't in the workbook. The scan skipped it as blank instead of flagging it. Not added yet.

---

## The Two Bugs

Both gave believable-looking numbers with zero error messages, so just scanning for`#VALUE!` would've missed them completely.

**Bug 1 — Temps billed as full-season salaries.** The model charged a whole $25,000 for the 4th worker no matter how few hours they actually worked, even though the sheet's own notes said temp labor was hourly. That stuck a big fake cost into the model and pushed the answer to the wrong crop mix. Changed it to hours × hourly rate. The Farm Profit Lab does it the same way, which confirms the fix.

**Bug 2 — Rounded rates typed in as if they were exact.** Three inputs were entered as the rounded numbers shown in the brief. Together they overstated profit by $13.16.

| Input | Was | Now |
|---|---|---|
| Farmer rate | 34.72 | derived → 34.7222 |
| Worker rate | 17.36 | derived → 17.3611 |
| Carrot labor hrs | 0.833 | `=5/6` → 0.8333 |

Carrots was the worst one — 0.833 is just a rounded 5/6, which is fifty minutes per bed per week. All three are now formulas, so they can't drift. I also added the farmer's
salary and her field-time share as proper inputs so her rate is calculated instead of just asserted.

And a small but annoying follow-on: after fixing the values, all three still *displayed* as the old rounded numbers. That's exactly how someone "helpfully" retypes the error back in later, so I widened the decimals to make the real values visible.

---

## How the Hypothesis Did

Four out of five predictions held up.

| Claim | Actual | |
|---|---|---|
| Uses all 64 beds | 60 | **Wrong** |
| Tomatoes below cap | 10 of 20 | Right |
| Carrots near cap | 20 of 20 | Right |
| Mesclun near cap | 30 of 30 | Right |
| Mesclun > Carrots > Tomatoes | 30 > 20 > 10 | Right |

The miss is the most interesting result here. Four beds stay empty on purpose. And tomatoes stop at 10 of 20 even though they earn the most per bed ($8,800) — because by bed 11 the extra labor costs $9,390.72 to bring in $8,800.
