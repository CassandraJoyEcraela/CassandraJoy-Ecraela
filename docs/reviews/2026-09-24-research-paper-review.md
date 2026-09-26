<!-- PR TARGET: https://github.com/CassandraJoyEcraela/CassandraJoy-Ecraela | Individual Research Paper -->
# Individual Research Paper — pre-deadline read

**What I read.** `docs/briefs/research-brief.md` and `capabilities/economic-research/spec.md` in
full · `capabilities/economic-research/README.md` · `data/README.md` · the research-paper entry in
`prompt-log.md` · the file tree and the commits behind the brief and spec.

**What I did not open this pass.** Your Case 1 files, `AGENTS.md`, `CLAUDE.md`, `RESUME.md`,
`README.md`. If something in those changes an item below, say so and I will look.

---

You did what I asked. One question, not three; offshoring and AI framed as the same fall in the cost
of a unit of customer service arriving through two channels; a measured series — BLS OEWS,
SOC 43-4051, ten years — at the center; and company statements about AI kept as a separate,
non-numeric series so that the gap between what firms say and what the employment numbers show can
be a finding rather than something smoothed over. Your spec's success criteria say that last part in
your own words, and it is the best sentence in either file. The items below are what the design still
needs before you pull data, in the order they depend on each other.

**An employment series cannot tell AI from offshoring, and your spec should say so.** Both channels
predict the same thing — fewer domestic CSR jobs, flat or falling wages — so a decline in the OEWS
line, however sharp, is consistent with either story. The only thing in your design that separates
them is timing: your second falsification condition, whether the numbers moved before or after the AI
statements appear. That is a legitimate test, but it is a timing test, and the paper should call it
one. Two ways to strengthen it. Write your first condition operationally — fit the 2016–2021 trend,
project it forward, and state in advance how far 2022–2025 has to sit below the projection to count as
a break — so "smooth continuation" is a number, not a judgment. And ask whether any measured series
exists for the offshoring channel itself; if not, say in the spec that the two channels are
distinguished by timing alone, which is an honest limitation and a better paper than one that implies
more.

**Elasticity of labor demand needs a price, and your data plan has none.** The concept measures how
much CSR employment falls when a substitute gets cheaper; nothing in the plan measures the price of
the substitute — offshore wages or the cost of the software. Either find a proxy you can defend, or
drop the concept. Labor as an input with substitutes, plus structural versus cyclical displacement,
carry the argument on their own.

**Who acts on the answer?** Recommendation is the heaviest criterion and neither file names a
decision-maker. A head of customer operations deciding whether to hold domestic headcount, a
workforce board deciding what to retrain toward, a policymaker — pick one, and the recommendation
falls out of the finding.

**Decide the LinkedIn postings before you draft.** The spec marks the fourth figure "pending
accessibility to data" and your log says the same. Confirm you can get the series — and that it is a
measured series, not an article about one — or cut the postings from both files so the paper never
promises them.

**Pull OEWS now.** `data/` holds only a placeholder. Each OEWS year is a May snapshot; say so in the
caption, so your era shading is not read as calendar years. Record source, retrieval date and any
transformation per your `data/README.md`.

Your first question — the offshoring history — is background in the brief's Topic section, which is
the evidence-section role I suggested. Keep it there.

**In order:**

1. Write the break test as a number, and state in the spec that the channels are separated by timing.
2. Find a price for the substitute, or drop the elasticity concept.
3. Name the decision-maker.
4. Confirm or cut the LinkedIn postings.
5. Pull the OEWS series into `data/` with source and retrieval date.
