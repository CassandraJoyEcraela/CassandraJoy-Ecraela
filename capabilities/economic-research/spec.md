# Spec: AI Automation & Customer Service Employment

**Course:** BUS620 — Individual Research Paper **|** **Capability:** economic-research **|** **Status:** draft (pending approval & feedback from Professor Adam)

## Data Sources

- **BLS OEWS employment and wage data, SOC 43-4051 (Customer Service Representatives)** — annual data, 2016 through 2025 (the latest year currently published). This is the core measured series: what actually happened to CSR jobs and pay over a window that spans both the offshoring era and the AI era.
- **LinkedIn job postings data for CSR roles, by year, 2016–2025** — a leading indicator of hiring intent, tracked alongside the BLS series rather than blended into it.
- **A timeline of company statements attributing layoffs or hiring freezes to AI** — a non-numeric series built by collecting dated company statements (earnings calls, press releases, news coverage) that name AI as a reason for CSR headcount changes. Kept separate from the two measured series above so it can be compared against them, not folded in.

## Model / Figures

- **Main figure — CSR employment over time (2016–2025):** a single time-series line showing CSR employment by year, with the offshoring era and the period since AI-attribution statements began (~2022–2023) visually distinguished (e.g., shading or a marked line). This is the figure the whole argument depends on — it needs to make a break-or-continuation call visible at a glance.
- **Overlay — AI statement timeline against the employment line:** the dated AI-attribution statements plotted as markers on the same timeline as the employment figure, so it's visible whether they cluster before, during, or after any shift in the employment line.
- **Supporting figure — wage trend alongside employment:** a second line (or panel) showing CSR wages over the same window. A wage decline without a matching employment decline (or vice versa) would tell a different story than both moving together, so this figure exists to catch that.
- **Optional — job postings vs. realized employment:** if the LinkedIn postings data is clean enough to chart, a comparison of postings volume against realized BLS employment can show whether hiring intent moved ahead of actual headcount changes. (pending accessibility to data) 

## Success Criteria

A finished paper meets this spec if it:

- **States its answer plainly, early.** The reader shouldn't have to wait until the conclusion to learn whether the evidence says AI is behaving like offshoring or differently.
- **Makes the main figure legible on its own.** Someone looking only at the employment chart (with the AI-statement overlay) should be able to see the claim being made, without needing the surrounding text to explain it.
- **Keeps the narrative and measured series distinct.** What companies say about AI and what the employment/wage numbers show are reported separately, and the gap between them — if there is one — is treated as a finding, not smoothed over.
- **Passes its own falsification test.** The paper is testing itself against two ways it could be wrong:
  - If the 2022–2025 portion of the employment/wage trend is a smooth continuation of the 2016–2021 trend — no acceleration, no visible break — that undercuts the claim that anything new is happening in the AI years.
  - If job postings or employment started falling well *before* AI-attribution statements appear in the timeline, that suggests AI is a post-hoc label on cuts that were already happening for other reasons.
