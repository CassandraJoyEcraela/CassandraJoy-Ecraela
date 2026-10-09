# Spec: AI Automation & Customer Service Employment

**Course:** BUS620: Individual Research Paper **|** **Capability:** economic-research **|** **Status:** Committed and revised with Professor Adam's feedback

## Data Sources

- **BLS OEWS data for customer service reps (SOC 43-4051):** one employment number and one wage number per year, 2016 through the latest May BLS has published. This is the main measured data in the paper: what actually happened to CSR jobs and pay. A few things to know about it:
  - Each year is a snapshot from May, not an average of the whole year. 
  - Each year's estimate blends survey responses from the last three years, so it moves slowly and the exact timing of a change is blurry. The paper says this plainly.
  - It can't tell us whether a drop in jobs came from offshoring or AI. Both would look the same: fewer jobs and flat or falling pay. The only thing that separates the two stories in this paper is timing.
- **Indeed Hiring Lab's Customer Service job postings index, from FRED (series ID: IHLIDXUSTPCUSTSERV):** a daily measure of CSR job postings, adjusted for normal seasonal swings, where February 1, 2020 is set to 100. Free to use if Indeed Hiring Lab is credited. It's a hint of what companies plan to do about hiring, and it sits next to the BLS data, not mixed into it. It starts in February 2020, so it covers the AI years and the run-up, but not the 2016–2021 baseline. For the timing test, I average it into calendar quarters and look at how it changes from one quarter to the next, never at its level, because the level only means something compared to that February 2020 starting point.
- **CPI for all urban consumers, all items, not seasonally adjusted, from FRED (series ID: CPIAUCNS):** used only to turn wages into inflation-adjusted dollars. It's a helper, not a finding.
- **A timeline of companies blaming AI for layoffs or hiring freezes:** a list I build myself. It's kept separate from the measured data on purpose, so I can compare the two instead of blending them. What goes on it is decided by the rule below, written before I collect anything.

## Wage Measure

Decided before I pull any data. It doesn't change afterward.

- **What I use:** the median annual wage for SOC 43-4051, from the national table for each May.
- **The main line is inflation-adjusted:** every year's median gets converted into dollars of the latest May in the data, using the CPI series above. Real wage = nominal wage × (CPI in the latest May ÷ CPI in that year's May). I use May CPI values because the BLS numbers are May snapshots.
- **The raw numbers stay:** nominal wages stay in the data file and show up in a table next to the figure.
- **The caption says so:** it names the base May and says wages are adjusted with CPI-U.
- **One limit:** CPI-U tracks prices in general, not the cost of living for customer service workers specifically, so the real wage is a rough guide to buying power.

## How a Statement Gets on the AI Timeline

This rule is written before I collect anything, and it applies the same way to every candidate.

- **Where I look:** earnings call transcripts, company press releases and SEC filings, and major news outlets that directly quote or cite the company.
- **What counts:** an official company source or a named executive says AI or automation is a reason for cutting, freezing, or not replacing jobs. The company is US-based or has customer service workers in the US.
- **What doesn't count:** analyst guesses, and a reporter's own theory about why a company cut jobs.
- **Which roles count:** customer-facing service jobs, meaning jobs whose main work is answering customers' questions, requests, or complaints by phone, chat, email, or in person. This matches the BLS definition of the job I'm measuring, which leaves out jobs that are mainly sales, installation, repair, or technical support. Only these statements go on the timeline and set the clock in the timing test.
- **Search terms (set now):** AI or automation, together with any of: customer service, customer support, customer care, customer experience, customer-facing, client services, contact center, call center; together with any of: layoffs, hiring freeze, headcount.
- **Logged but not counted:** anything that doesn't fit the role rule goes in a separate log with a one-line reason. That includes general AI and layoffs statements and statements about tech support, IT, sales, or repair jobs. They don't set the clock in the main test.
- **Extra search terms for the tech support check (set now):** AI or automation, together with any of: technical support, tech support, IT support, help desk, IT department; together with any of: layoffs, hiring freeze, headcount. These follow the same rules for sources, dates, and entries, and go in the separate log.
- **When in doubt, don't count it.** A borderline statement goes in the separate log with a one-line reason. I decide by the rule, not by what helps my answer.
- **Date:** the day the statement was first made public, not the day the layoffs happened.
- **Every entry has:** the date, the company, a source link, which log it's in, the exact words the company used for the role, and a short note in my own words about what was said.
- **Honest limit:** this is a documented search, not a complete count. "The first statement" means the earliest one I found under this rule.

## Figures

- **Main figure: CSR employment, 2016–2025.** One line, one point per year. It's split into an offshoring era (2016–2021) and an AI era (2022–2025), but the split comes from the break test's result, not from where the line looks like it bends. The pandemic years (2020 and 2021) are marked, and the caption says each point is a May snapshot.
- **Overlay: AI statements on the employment chart.** A marker for each dated customer-facing statement, on the same chart, so you can see whether they show up before, during, or after any shift.
- **Supporting figure: wages next to employment.** Inflation-adjusted median wages over the same years, with the raw dollar numbers in a table beside it. If real wages fall while employment doesn't (or the reverse), that's a different story than both dropping together, and this figure catches it.
- **Job postings vs. employment (2020–2025):** the Indeed index plotted against BLS employment over the years they both cover, to see whether hiring plans moved before actual headcount did. The March and April 2020 crash is marked so it doesn't get read as a lasting drop. The postings data can be downloaded from FRED with no login, and it only goes back to 2020.

## Success Criteria

A finished paper meets this spec if it:

- **Says what it found, early and plainly.** A reader shouldn't have to reach the conclusion to learn whether AI is acting like offshoring or something different.
- **Makes the main figure stand on its own.** Someone who only looks at the employment chart with the AI markers should see the paper's claim without reading the text first.
- **Keeps what companies say separate from what the numbers show.** If they don't match, that gap is reported as a finding, not smoothed over.
- **Says plainly what it can't prove.** The BLS numbers alone can't separate an AI-driven decline from an offshoring-driven one. The paper only separates them by timing, and it says that's a real limit of the design.
- **Sets its rules before it sees the data.** The break test, the timing test, the wage measure, and the statement rule are all written down and committed before I pull any numbers, and none of them changes afterward. If I later think one was wrong, I keep the original, say what I'd change and why, and report results both ways.
- **Owns the break test's limits, not just its result.** Only six years of data sit behind the test, and two of them are pandemic years, which adds noise and can widen the margin. The paper keeps all six years, says the pandemic is part of the noise, and doesn't switch baselines after seeing results. If 2022–2025 stays inside the margin, the paper says "the test didn't detect a break," never "nothing happened."
- **Answers a real decision.** The recommendation is written for a head of customer operations deciding whether to hold current CSR headcount, cut further, or bring jobs back onshore. What the two tests find decides which one the paper recommends, not the other way around.
- **Passes its own tests, with numbers set in advance:**
  - **Break test:** Fit a straight trend line (OLS regression) to CSR employment for all six baseline years, 2016–2021. I keep the pandemic years in on purpose. Fitting only 2016–2019 would leave too little data to judge normal ups and downs, so the floor would be too wide to catch anything. The cost is that the pandemic adds noise and widens the floor, and the paper says so. This is the only version of the test I run. Then:
    - Extend the line through 2025.
    - Use how much the 2016–2021 numbers bounced around the line to set a floor for 2022–2025, at a 90% cutoff. Only drops matter, so it's a one-sided floor.
    - Two years in a row below the floor counts as a real break. One bad year doesn't.
    - If 2022–2025 never has two years in a row below the floor, that's a smooth continuation, with nothing new to explain.
    - The paper reports the actual floor and the actual 2022–2025 numbers, in the text and the figure. Landing inside the floor gets described as "the test didn't detect a break," never "nothing happened."
  - **Timing test:** Did the decline start before companies began blaming AI? Both series are read as changes, not levels, and a fall that starts in 2020 or 2021 doesn't count on either one, so the pandemic can't pass for an early warning.
    - **Postings:** average the daily index into calendar quarters. A quarter is "falling" if its average is at least 3% below the previous quarter's. The series "starts falling" at the first of two or more falling quarters in a row. "Well before" means that run starts at least two quarters before the quarter of the first customer-facing AI statement.
    - **Threshold check:** 3% is the main threshold. I also report the result at 1% and 5%, decided now, so a reader can see whether the answer depends on the exact number. If it flips, the paper says the timing result is sensitive to the threshold.
    - **Employment:** a year is a "decline year" if its May estimate is lower than the previous May's. Employment "starts falling" at the first of two decline years in a row. "Well before" means that first fall comes at least one calendar year before the year of the first customer-facing AI statement. The BLS data is blurry on timing, so postings is the sharper clock, and the paper says where the two disagree. If the first statement is too early for employment to show a fall "well before" it, the paper says employment can't answer the timing question.
    - **Tech support check:** the main test uses the earliest customer-facing statement as the clock. I also report what the result would be if the earliest tech support or IT statement from the separate log set the clock instead. If the answer is the same, that strengthens it. If it changes, the paper says so and notes that the broader clock covers jobs the BLS occupation leaves out.
    - **Reading the result:** if either series starts falling well before the first statement, AI may be a label put on cuts that were already happening. If a fall starts within two quarters of the first statement (postings) or within a year (employment), before or after, the timing is inconclusive. If both series start falling after the first statement, that fits AI being a real trigger, though it doesn't prove it.

## Revision notes

The original wording above is unchanged. These notes record where the paper now does something the spec did not say, and why.

### 2026-10-08 — Break test: the floor formula

**Original wording (kept above):** "Use how much the 2016–2021 numbers bounced around the line to set a floor for 2022–2025, at a 90% cutoff. Only drops matter, so it's a one-sided floor." and "This is the only version of the test I run."

**What the paper does:** The wording did not say whether the cushion below the trend line stays the same every year or grows the further out a year is. The paper builds both and reports them side by side in Appendix A. This note replaces "the only version of the test I run" with two versions.

- **Trend:** a straight line (OLS) through the six baseline years, 2016–2021, pandemic years kept in.
- **Floor formula:** floor = trend − t × s. Here s is the typical bounce of the baseline years around the line (about 76,000 jobs), and t = 1.533 is the multiplier for a 90% one-sided cutoff with six data points.
- **Fixed floor:** the cushion (t × s, about 116,500 jobs) is the same every year. This is the literal reading of the original wording.
- **Forecast floor:** the same cushion, multiplied by a factor that grows the further a year is from the middle of the baseline years (about 1.4× in 2022 up to 1.9× in 2025). A line built on six points is less trustworthy farther out, so the cushion should grow.
- **Primary version:** the forecast floor. Both are reported so the conclusion can be checked.

**What did not change:** the 90% one-sided cutoff, two years in a row to count as a break, all six baseline years kept, and "did not detect a break" (never "nothing happened") when 2022–2025 stays inside the floor.

### 2026-10-08 — Timing test: a threshold with no run

**Original wording (kept above):** "I also report the result at 1% and 5%, decided now, so a reader can see whether the answer depends on the exact number. If it flips, the paper says the timing result is sensitive to the threshold."

**What the paper does:** At the 5% threshold the postings index never falls two quarters in a row after 2021, so there is no start date to compare with the first statement. The spec did not say how to report that. The paper reports it as "no run": that threshold cannot answer the timing question. It is not counted as the result flipping, and it is not described as "postings never fell." The timing conclusion rests on the thresholds that do produce a run (1% and 3%), where it holds.

**What did not change:** the 1%, 3% (primary) and 5% thresholds, and the rule that a run is two or more falling quarters in a row, ignoring any fall that starts in 2020 or 2021.
