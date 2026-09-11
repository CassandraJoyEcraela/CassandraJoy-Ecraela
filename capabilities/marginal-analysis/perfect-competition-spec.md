---
type: spec
engagement: case-1-perfect-competition
capability: marginal-analysis
date: 2026-09-08
status: draft
built_with: claude
---

# Perfect Competition — Spec

## Purpose
Build a constrained-optimization model using Excel Solver that solves for the amount of beds that should be planted for tomatoes, carrots, and mesclun to maximize season profit. This is subject to bed caps, costs, and labor availability for one season - which is all specified below. Build the Excel Workbook to to test the hypothesis committed in
`docs/briefs/perfect-competition-brief.md` No one of the outputs should exceed the cost, labor, or bed caps specified below.

## Inputs
| Named Range | Source | Value | Unit |
|---|---|---|---|
| `season_weeks` | Case brief | 36 | weeks |
| `total_beds` | Case brief | 64 | beds |
| `fixed_costs` | Case brief | 20,000 | $ |
| `farmer_hours` | Case brief (implied: $50,000 ÷ 720 hrs) | 720 | hrs/season |
| `farmer_rate` | Case brief | 34.72 | $/hr |
| `worker_hours_each` | Case brief | 1,440 | hrs/season |
| `worker_rate` | Case brief | 17.36 (implied: $25,000 ÷ 1,440 hrs) | $/hr |
| `max_workers` | Case brief | 4 | workers |
| `tomato_max_beds` | Case brief | 20 | beds |
| `tomato_price` | Case brief | 8,800 | $/bed |
| `tomato_labor_hrs_wk_bed` | Case brief | 2.5 | hrs/wk/bed |
| `tomato_fert_cost` | Case brief | 880 | $/bed |
| `tomato_dim_rate` | Case brief | 10.00% | per bed |
| `carrot_max_beds` | Case brief | 20 | beds |
| `carrot_price` | Case brief| 2,094 | $/bed |
| `carrot_labor_hrs_wk_bed` | Case brief | 0.833 | hrs/wk/bed |
| `carrot_fert_cost` | Case brief | 440 | $/bed |
| `carrot_dim_rate` | Case brief | 2.50% | per bed |
| `mesclun_max_beds` | Case brief | 30 | beds |
| `mesclun_price` | Case brief | 2,700 | $/bed |
| `mesclun_labor_hrs_wk_bed` | Case brief | 1.25 | hrs/wk/bed |
| `mesclun_fert_cost` | Case brief | 880 | $/bed |
| `mesclun_dim_rate` | Case brief | 1.25% | per bed |

**Decision variables (Solver's changing cells):**

| Named Range | Meaning |
|---|---|
| `tomato_beds` | number beds of tomatoes planted |
| `carrot_beds` | number beds of carrots planted |
| `mesclun_beds` | number beds of mesclun planted |

## Structure
- Sheet #1: `Inputs` sheet with tables of each data point provided
- Sheet #2: `Labor & Cost` sheet computing hours and cost per crop
- Sheet #3: `Optimization` sheet with the three decision cells, the objective, the answers compared to each claim, and the constraints that led to that conclusion

## Calculation logic
The engine of the whole model is one formula - hours of labor needed for q beds of a crop: hours(q) = q × hrs-per-week-per-bed × 36 weeks × (1 + dim%)^q
Total Labor Hours Per Crop
```
tomato_labor_hours = tomato_beds × tomato_labor_hrs_wk_bed × season_weeks × (1 + tomato_dim_rate) ^ tomato_beds
carrot_labor_hours = carrot_beds × carrot_labor_hrs_wk_bed × season_weeks × (1 + carrot_dim_rate) ^ carrot_beds
mesclun_labor_hours = mesclun_beds × mesclun_labor_hrs_wk_bed × season_weeks × (1 + mesclun_dim_rate) ^ mesclun_beds
total_labor_hours = tomato_labor_hours + carrot_labor_hours + mesclun_labor_hours
```

Pending formulas (still figuring out how to create the formulas)
- how `total_labor_hours` gets split between the farmer's 720 hours and temp-worker hours (the farmer's hours will get used first, per the
case's details
- how many temp workers are needed. this needs to be a whole number that doesn't exceed the `max_workers` (which is 4 workers)
- the blended labor rate (total labor dollars ÷ total hours, the other stated convention)
- fertilizer cost per crop
- revenue per crop
- total profit = revenue − labor cost − fertilizer cost − fixed_costs

## Validation rules
- `tomato_labor_hours` at `tomato_beds = 1` matches a hand calculation:  1 × 2.5 × 36 × 1.10
- At least one intermediate marginal-cost value cross-checked against the   Farm Profit Lab tool
- Solver run from two starting points (0/0/0 and 20/0/0) returns the same answer
- Model reproduces published check figures: mix = 10 tomatoes / 20 carrots  / 30 mesclun, season profit = $42,762
- No error cells; every calculated cell contains a formula referencing named ranges, not a pasted value

## Outputs
- `tomato_beds`, `carrot_beds`, `mesclun_beds`
- 'tomato_labor_hours,' 'carrot_labor_hours,' 'mesclun_labor_hours,' 
- `total_profit`

## Audit findings
[Will be filled in after the workbook is created]
