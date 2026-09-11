| type       | spec                        |
| ---------- | --------------------------- |
| engagement | case-1-perfect-competition   |
| capability | marginal-analysis            |
| date       | 2026-09-08                   |
| status     | approved-for-build           |

# Perfect Competition Spec

## How to use this document

Paste this entire document into Claude with a spreadsheet open. It is self-contained —
no other files or context are required. Claude will build the workbook, verify it, and
hand you the exact Solver dialog entries to run.

**Claude cannot run Excel Solver.** Solver is a manual add-in and is not scriptable.
Claude builds the model, wires the constraints, and tells you exactly what to type into
Data → Solver. You run it. Claude then verifies the result independently.

Do not tell Claude the expected answer. The point of the exercise is to derive it.

---

## The scenario

A market farmer is planning one growing season and must decide how many garden beds to
plant with each of three crops. She wants the mix that maximizes season profit.

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

These are all the facts. There are no others. Do not introduce outside assumptions
about yields, prices, weather, or crop rotation.

**How diminishing returns works in this model:** revenue per bed stays constant, but
each additional bed of a crop takes proportionally more labor to work. For a crop with
`q` beds planted, the escalation applies from the first bed:

`hours(q) = q * labor_hrs_wk_bed * season_weeks * (1 + dim_rate)^q`

**Scope of the farmer's salary:** charge only the field half of her $50,000 to the
model — 720 hours at her field rate, which must come to exactly $25,000. The non-field
half is out of scope and does not go into fixed costs.

## The hypothesis to test

The farmer's engagement brief predicts the following. Build the model so each claim is
tested against the solved optimum. **These are predictions, not facts.** Any of them may
turn out to be wrong, and a failed claim is a legitimate finding — do not tune a test so
that it passes.

1. The optimal plan uses all 64 beds
2. Tomatoes come in below their 20-bed cap
3. Carrots land near their 20-bed cap
4. Mesclun lands near its 30-bed cap
5. Planted beds rank Mesclun > Carrots > Tomatoes

---

## Critical: the three rounded rates

The scenario above displays three rates as rounded values. **Entering them as typed
constants will produce a wrong answer.** Derive all three by formula:

| Input | Scenario shows | Derive as | Evaluates to |
|---|---|---|---|
| `farmer_rate` | 34.72 | `farmer_salary * farmer_field_share / farmer_hours` | 34.7222… |
| `worker_rate` | 17.36 | `worker_flat_cost / worker_hours_each` | 17.3611… |
| `carrot_labor_hrs_wk_bed` | 0.833 | `5/6` | 0.8333… |

Carrots at 0.833 is a rounded display of 5/6 — fifty minutes per bed per week.

Format all three to show at least 4 decimal places. Under a 2-decimal format they
render as the rounded figures, which invites a future editor to retype the rounded
value and silently reintroduce the error.

---

## Workbook structure

Three worksheets, in this order.

1. **`Inputs`** — all assumptions as named ranges. Only the three derived rate cells
   may contain formulas.
2. **`Labor & Cost`** — all crop-level calculations and labor allocation logic.
3. **`Optimization`** — decision variables, objective function, Solver setup
   instructions, constraint check table, outputs, hypothesis test, recommendation.

Create every named range listed below using exactly the names given. Formulas
throughout must reference named ranges, not raw cell addresses, so the model stays
readable.

The row numbers given are a recommended layout. The named ranges and the two Solver
anchors — changing cells at `Optimization!$C$5:$C$7` and objective at
`Optimization!$C$11` — are required. Keep the three decision variables contiguous so
Solver can take them as one range.

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

Layout is `A` = named range, `B` = value, `C` = unit. Section headers in column A with
a `Named Range | Value | Unit` label row beneath each.

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

Temporary labor is an **hourly variable cost on hours actually used**. Workers are not
charged as fixed seasonal salaries.

| Named Range | Cell | Formula |
|---|---|---|
| `farmer_labor_cost` | B16 | `=farmer_hours_used*farmer_rate` |
| `temp_labor_cost` | B17 | `=temp_hours_used*worker_rate` |
| `total_labor_cost` | B18 | `=farmer_labor_cost+temp_labor_cost` |
| `blended_labor_rate` | B19 | `=IF(total_labor_hours=0,0,total_labor_cost/total_labor_hours)` |

**Do not write** `temp_labor_cost = temp_workers_needed * worker_flat_cost`. Charging a
full $25,000 seasonal salary for a partially utilized worker introduces a large false
step cost into the objective function and drives Solver to a different, wrong answer.
This is the single most likely way to get this model wrong.

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

Add a check row at C8: `=tomato_beds+carrot_beds+mesclun_beds`, labeled "Total beds
planted". All three variables must be integer and >= 0.

### Objective Function (A10:C11)

`total_profit` at C11:

`=total_revenue-total_labor_cost-total_fertilizer_cost-fixed_costs`

### Solver Setup Block (A13:C25)

A text block giving the user the exact entries to type into Data → Solver, since Claude
cannot run it. State the objective cell, the changing-cell range, each constraint as a
concrete cell-reference pair, the solving method, and step-by-step instructions
including both required starting points.

### Labor Outputs (A28:B36)

Each a formula pulling the named range from `Labor & Cost`: `tomato_labor_hours`,
`carrot_labor_hours`, `mesclun_labor_hours`, `total_labor_hours`, `farmer_hours_used`,
`temp_hours_used`, `temp_workers_needed`.

### Financial Outputs (A38:B43)

`total_revenue`, `total_labor_cost`, `total_fertilizer_cost`, `fixed_costs`,
`total_profit`.

### Hypothesis Test (A45:D51)

Columns: Claim | Expected | Actual | Pass/Fail. One row per claim from the hypothesis
list above. Expected is `Yes` for all five. **Actual and Pass/Fail must be formulas**
reading the decision variables — never pre-filled values.

Example for claim 1:
`Actual: =tomato_beds+carrot_beds+mesclun_beds`
`Pass/Fail: =IF(tomato_beds+carrot_beds+mesclun_beds=total_beds,"Pass","Fail")`

"Near cap" is undefined in the scenario. Implement it as exact equality to the crop's
`*_max_beds` and flag the ambiguity in a cell note — if a tolerance was intended, it
could change the outcome.

### Constraint Check Table (A53:F61)

Columns: Constraint | Left-hand side | LHS value | Op | RHS value | Status. One row per
constraint below. LHS and RHS must be formulas referencing named ranges, never typed
numbers. Status is `=IF(Cn<=En,"OK","VIOLATED")`. Roll up at C61 with
`=IF(COUNTIF(F55:F60,"VIOLATED")=0,"FEASIBLE","INFEASIBLE")`.

Point the Solver constraint dialog at these cells. This makes the constraint set
auditable without opening Solver.

### Final Recommendation (A63 onward)

A short written block, derived from the solved model: the recommended crop mix, the
resulting profit, which constraint is actually binding at the optimum, and the economic
reason the model stops adding beds of the highest-revenue crop before reaching its cap.

---

## Solver configuration

- **Objective cell:** `$C$11` (`total_profit`), set to **Max**
- **Changing cells:** `$C$5:$C$7`
- **Solving method:** **Evolutionary**

### Constraints

Reference named ranges on the right-hand side, not literal numbers, so changing an
input propagates through.

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

Worker Limit is arithmetically redundant once Labor Capacity is enforced, since
`total_labor_capacity` already implies at most `max_workers`. Keep it as a readability
check and note that it is redundant.

### Use Evolutionary, not GRG Nonlinear

`ROUNDUP` in `temp_workers_needed` and `MIN`/`MAX` in the labor allocation make the
profit surface discontinuous. GRG Nonlinear assumes smooth gradients and will stall on
whichever step plateau it starts from, reporting a local result as though it had
converged. The exponential terms in the labor formula would not by themselves rule out
GRG — the step functions do.

Evolutionary is stochastic and can settle before reaching the global optimum. If runs
from different starting points disagree, raise Max Time without Improvement and
re-solve.

---

## Validation

Every check is answer-independent — these verify mechanics, not a known result. Run all
of them and report the outcome of each.

1. **Unit labor check.** Set `tomato_beds = 1`. `tomato_labor_hours` must return
   `1 * 2.5 * 36 * 1.10` = 99.0 hours exactly.
2. **Zero check.** Set all three decision variables to 0. Every crop-specific labor,
   revenue, and fertilizer cell returns 0, and `blended_labor_rate` returns 0 rather
   than `#DIV/0!`.
3. **Derived rate check.** Read back the *rendered* text, not the underlying value:
   `farmer_rate` displays 34.7222, `worker_rate` 17.3611,
   `carrot_labor_hrs_wk_bed` 0.8333. If any shows the rounded figure, the number
   format is too narrow — widen it.
4. **Farmer cost check.** At any solution where `total_labor_hours >= 720`,
   `farmer_labor_cost` equals exactly $25,000.00.
5. **Error scan.** No `#REF!`, `#VALUE!`, `#DIV/0!`, or `#NAME?` anywhere.
6. **No hardcoded results.** Every calculated cell contains a formula. Typed constants
   appear only in the designated input cells on `Inputs`.
7. **Feasibility.** At the reported solution, C61 reads FEASIBLE.
8. **Convergence check.** Run Solver from starting points 0/0/0 and 20/0/0. Both must
   return the same bed mix and the same profit. Record both runs.
9. **Independent verification.** The feasible space is small — at most 21 x 21 x 31
   integer combinations. Enumerate it exhaustively outside Excel using the same
   formulas and constraints, and confirm Solver reached the global maximum. Report the
   margin between best and second-best mix, so the reader knows whether Solver settling
   early would be visible. **Do not write the enumerated result into the workbook** as
   an input or benchmark — it is a check on Solver, not part of the model.

## Reporting

When finished, report: the solved crop mix and profit, the outcome of each validation
check, which constraint binds at the optimum, and which hypothesis claims passed or
failed. State plainly which ranges were re-read to verify and which were not.

If a hypothesis claim fails, say so directly and explain the economics. A failed
prediction is the most interesting output this model can produce.
