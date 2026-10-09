# Cassandra Joy Ecraela — feedback, sweep of 2026-10-05

Mahalo, Cassie, for the note on #6. Below is my read of the 3 October draft, with the figure you fixed beside it; it comes as its own pull request so that everything from this round sits in one place.

This pull request answers #6.

## Individual Research Paper — pre-deadline read

**What I read.** `drafts/2026-10-03-research-paper-draft.md` in full · `drafts/fig1_employment_vs_trend_paper.png` · `data/employment_and_wages.md` · `docs/briefs/research-brief.md` and `capabilities/economic-research/spec.md`, checked for changes since my last read · the commits since my last read.

**What I did not open this pass.** The Word version of the paper and its Appendices A–C, which are not in the repository · the data spreadsheets I traced last time · `prompt-log.md` · your Case 1 files. If something in those changes an item below, say so and I will look.

---

The draft does what the last round asked of it. It reports the break test under both bands and says why you chose the forecast band. It says plainly that the 5 percent threshold was never met. And the new figure carries the size of the decline in its caption, 11.1 percent below the 2019 peak, which traces to `data/employment_and_wages.md`. The recommendation, to hold headcount and manage through attrition, retraining and warning signs set in advance, answers the decision your brief poses for a head of customer operations.

**When does employment start falling?** The draft says "Employment's first two straight declines start in 2023." Your own `data/employment_and_wages.md` shows 2020 (2,833,250) and 2021 (2,787,070) both below 2019. Are the pandemic years set aside, and if so, does the paper say so where it makes the claim? The timing test depends on a reader knowing which years count.

**What, other than timing, could tell AI from offshoring?** The paper's own frame is that the two are the same substitution and "only timing separates them." Is there evidence that would move with one and not the other, something offshoring would leave behind that AI would not, or the reverse? Is any of it within reach in the time you have, or should the paper say plainly that the two cannot be separated with these data? Either answer is honest; the paper should give one.

**Close the open source items.** "Uber (2026) is pending" is still in the draft: resolve it or drop it. Founder Reports (n.d.) is an aggregator; is there a primary source, a filing or the company's own announcement, for the C.H. Robinson cut? And the brief still says firms began blaming AI "since around 2022–2023"; bring that line into line with the timeline the paper now reports. Several of the paper's numbers, including the floor-test gap, the posting-threshold quarters, the fall in postings, the drop in real pay in 2022, and the company-statement log, live only in the Word appendices. Committing those appendices, or the Word file, would let me trace them; that would help you, but it is not required.

**Bring the spec up to the paper.** The floor formula and the reporting of a threshold with no run are settled in the paper but not yet in the spec, which is unchanged since my last read. Your spec's own rule applies: keep the original wording, say what changed and why.

- **On github.com**: open `capabilities/economic-research/spec.md`, click the pencil icon, add the two notes, and commit.
- Or, in **Claude Code or Codex** opened in your portfolio repository: "Add a dated revision note to `capabilities/economic-research/spec.md` recording the floor formula and the no-run threshold rule as the paper states them. Keep the original wording and show me the note before you save it."

**In order:**

1. Answer in the text whether the 2020 and 2021 declines are set aside, and say so where the timing claim is made.
2. Decide whether anything besides timing can separate AI from offshoring, and say in the paper what you found.
3. Resolve or drop the Uber entry, find a primary source for the C.H. Robinson cut, and align the brief's "since around 2022–2023."
4. Record the floor formula and the no-run rule in the spec.
