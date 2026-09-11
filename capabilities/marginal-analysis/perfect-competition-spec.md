| type       | spec                        |
| ---------- | --------------------------- |
| engagement | case-1-perfect-competition   |
| capability | marginal-analysis            |
| date       | 2026-09-08                   |
| status     | approved-for-build           |

# Perfect Competition Excel Solver Model

## Purpose

Build an Excel workbook that uses Excel Solver to determine the profit-maximizing planting mix of tomatoes, carrots, and mesclun for one growing season.

The model must:

- maximize season profit
- determine optimal beds for each crop
- account for labor requirements, labor costs, fertilizer costs, and fixed costs
- respect all crop and resource constraints
- use integer bed quantities
- allow the hypothesis in the engagement brief to be tested against the calculated optimum

The workbook should return the crop mix that earns the highest season profit while satisfying all constraints.

## Inputs

Create an `Inputs` worksheet containing the following named ranges.

### General Inputs

| Named Range     | Value  | Unit  |
| ---------------- | ------ | ----- |
| `season_weeks`   | 36     | weeks |
| `total_beds`     | 64     | beds  |
| `fixed_costs`    | 20000  | $     |

### Farmer Inputs

| Named Range     | Value  | Unit       |
| ---------------- | ------ | ---------- |
| `farmer_hours`   | 720    | hrs/season |
| `farmer_rate`    | 34.72  | $/hr       |

### Temporary Labor Inputs

| Named Range         | Value  | Unit       |
| -------------------- | ------ | ---------- |
| `worker_hours_each`  | 1440   | hrs/season |
| `worker_rate`        | 17.36  | $/hr       |
| `max_workers`        | 4      | workers    |

### Tomatoes

| Named Range                 | Value   |
| ---------------------------- | ------- |
| `tomato_max_beds`            | 20      |
| `tomato_price`                | 8800    |
| `tomato_labor_hrs_wk_bed`    | 2.5     |
| `tomato_fert_cost`            | 880     |
| `tomato_dim_rate`             | 10.00%  |

### Carrots

| Named Range                 | Value   |
| ---------------------------- | ------- |
| `carrot_max_beds`            | 20      |
| `carrot_price`                | 2094    |
| `carrot_labor_hrs_wk_bed`    | 0.833   |
| `carrot_fert_cost`            | 440     |
| `carrot_dim_rate`             | 2.50%   |

### Mesclun

| Named Range                  | Value   |
| ----------------------------- | ------- |
| `mesclun_max_beds`            | 30      |
| `mesclun_price`                | 2700    |
| `mesclun_labor_hrs_wk_bed`    | 1.25    |
| `mesclun_fert_cost`            | 880     |
| `mesclun_dim_rate`             | 1.25%   |

## Decision Variables

These will be Solver changing cells.

| Named Range     | Meaning                          |
| ---------------- | --------------------------------- |
| `tomato_beds`    | beds planted with tomatoes        |
| `carrot_beds`    | beds planted with carrots         |
| `mesclun_beds`   | beds planted with mesclun         |

All decision variables must be:

- integer
- `>= 0`

## Workbook Structure

**Worksheet 1: Inputs**
Contains all assumptions and named ranges. No calculations beyond basic references.

**Worksheet 2: Labor & Cost**
Contains all crop-level calculations and labor allocation logic.

**Worksheet 3: Optimization**
Contains:
- Solver decision variables
- objective function
- constraint summary
- hypothesis comparison
- final recommendation

## Calculation Logic

### Crop Labor Formula

Labor requirements increase as additional beds of a crop are planted. For a crop with quantity `q`, the escalation factor applies beginning with the first planted bed:

```
hours(q) = q × labor_hrs_wk_bed × season_weeks × (1 + dim_rate)^q
```

**Tomato Labor**
```
tomato_labor_hours = tomato_beds × tomato_labor_hrs_wk_bed × season_weeks × (1 + tomato_dim_rate)^tomato_beds
```

**Carrot Labor**
```
carrot_labor_hours = carrot_beds × carrot_labor_hrs_wk_bed × season_weeks × (1 + carrot_dim_rate)^carrot_beds
```

**Mesclun Labor**
```
mesclun_labor_hours = mesclun_beds × mesclun_labor_hrs_wk_bed × season_weeks × (1 + mesclun_dim_rate)^mesclun_beds
```

**Total Labor**
```
total_labor_hours = tomato_labor_hours + carrot_labor_hours + mesclun_labor_hours
```

### Labor Allocation

Farmer hours are used first.

**Farmer Hours Used**
```
farmer_hours_used = MIN(total_labor_hours, farmer_hours)
```

**Temporary Hours Used**
```
temp_hours_used = MAX(0, total_labor_hours - farmer_hours)
```

**Temporary Workers Required** *(reporting calculation only — not a Solver decision variable)*
```
temp_workers_needed = IF(temp_hours_used = 0, 0, ROUNDUP(temp_hours_used / worker_hours_each, 0))
```

**Total Labor Capacity**
```
total_labor_capacity = farmer_hours + (max_workers × worker_hours_each)
```

### Labor Cost Calculation

Temporary labor is treated as an hourly variable cost. Workers are not charged as fixed seasonal salaries.

**Farmer Labor Cost**
```
farmer_labor_cost = farmer_hours_used × farmer_rate
```

**Temporary Labor Cost**
```
temp_labor_cost = temp_hours_used × worker_rate
```

**Total Labor Cost**
```
total_labor_cost = farmer_labor_cost + temp_labor_cost
```

**Blended Labor Rate**
```
blended_labor_rate = IF(total_labor_hours = 0, 0, total_labor_cost / total_labor_hours)
```

### Revenue

```
tomato_revenue = tomato_beds × tomato_price
carrot_revenue = carrot_beds × carrot_price
mesclun_revenue = mesclun_beds × mesclun_price
total_revenue = tomato_revenue + carrot_revenue + mesclun_revenue
```

### Fertilizer Cost

```
tomato_fertilizer_cost = tomato_beds × tomato_fert_cost
carrot_fertilizer_cost = carrot_beds × carrot_fert_cost
mesclun_fertilizer_cost = mesclun_beds × mesclun_fert_cost
total_fertilizer_cost = tomato_fertilizer_cost + carrot_fertilizer_cost + mesclun_fertilizer_cost
```

## Objective Function

**Total Profit**
```
total_profit = total_revenue - total_labor_cost - total_fertilizer_cost - fixed_costs
```

Solver should maximize `total_profit`.

## Solver Configuration

**Objective Cell:** `total_profit`, set to `MAX`

**Changing Cells:** `tomato_beds`, `carrot_beds`, `mesclun_beds`

**Constraints:**

| Constraint          | Rule                                              |
| -------------------- | -------------------------------------------------- |
| Bed Capacity          | `tomato_beds + carrot_beds + mesclun_beds <= 64`  |
| Tomato Cap            | `tomato_beds <= 20`                                |
| Carrot Cap            | `carrot_beds <= 20`                                |
| Mesclun Cap           | `mesclun_beds <= 30`                               |
| Labor Capacity        | `total_labor_hours <= total_labor_capacity`        |
| Worker Limit          | `temp_workers_needed <= max_workers`               |
| Non-Negativity        | `tomato_beds, carrot_beds, mesclun_beds >= 0`      |
| Integer Constraints   | `tomato_beds, carrot_beds, mesclun_beds = integer` |

**Solver Method:** GRG Nonlinear, because labor requirements contain exponential terms.

## Validation Requirements

1. At `tomato_beds = 1`, the workbook must return `1 × 2.5 × 36 × 1.10 = 99.0 hours`.
2. At `tomato_beds = 0`, `carrot_beds = 0`, `mesclun_beds = 0`, all crop-specific labor, revenue, and fertilizer costs equal zero.
3. The workbook contains no `#REF!`, `#VALUE!`, `#DIV/0!`, or `#NAME?` errors.
4. All calculated values use formulas — no calculated values may be hardcoded.
5. Run Solver from starting points `0/0/0` and `20/0/0`. The optimal solution should converge to the same result.

## Outputs

The Optimization sheet must display:

**Decision Variables:** `tomato_beds`, `carrot_beds`, `mesclun_beds`

**Labor Outputs:** `tomato_labor_hours`, `carrot_labor_hours`, `mesclun_labor_hours`, `total_labor_hours`, `farmer_hours_used`, `temp_hours_used`, `temp_workers_needed`

**Financial Outputs:** `total_revenue`, `total_labor_cost`, `total_fertilizer_cost`, `fixed_costs`, `total_profit`

**Hypothesis Test Section:**

| Claim                          | Expected | Actual         | Pass/Fail |
| -------------------------------- | -------- | -------------- | --------- |
| Use all 64 beds                  | Yes      | Solver result  | Pass/Fail |
| Tomatoes below cap               | Yes      | Solver result  | Pass/Fail |
| Carrots near cap                 | Yes      | Solver result  | Pass/Fail |
| Mesclun near cap                 | Yes      | Solver result  | Pass/Fail |
| Mesclun > Carrots > Tomatoes     | Expected | Solver result  | Pass/Fail |
````
