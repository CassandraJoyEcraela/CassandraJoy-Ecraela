<!-- PR TARGET: https://github.com/CassandraJoyEcraela/CassandraJoy-Ecraela | Stage 1.1 (2.5 pts) -->
# Stage 1.1 review — engagement brief · **80 / 100** (B-) · 2.00 / 2.5 pts

**Brief:** [`docs/briefs/perfect-competition-brief.md`](https://github.com/CassandraJoyEcraela/CassandraJoy-Ecraela/blob/main/docs/briefs/perfect-competition-brief.md)

> Graded 2026-08-31, first pass on this brief. Three of the four criteria are solid. The fourth is empty in a way that is worth ten minutes to fix.

| Criterion | Earned | Notes |
|---|---|---|
| Problem restated in your own voice | 27 / 30 | Clearly yours and it does something the stage asks for that almost nobody delivers: it says what happens if the decision goes badly, and it says it in a way that is about the business rather than the grade. "Farmers operate on such small profit margins that a bad decision could cost them the business." And then the sentence that makes it a one-shot decision: "Time is a resource they can't get back." That is the reason the mix cannot be revised mid-season, which is what makes the brief worth writing before the model. You have the price-taker framing right, the caps right, and the case parameters laid out in a clean table. The three points off are that the table does the work the prose should — the parameters are listed but never related to one another until the hypothesis section. |
| Hypothesis names a specific mix | 25 / 25 | 14 tomato, 20 carrot, 30 mesclun — 64 beds exactly, in the frontmatter and again in the body. Specific and committed. |
| Economic mechanism | 22 / 25 | Real reasoning, and one part of it is better than it looks. You considered splitting the remaining beds evenly between carrots and mesclun, then rejected it: mesclun earns more per bed than carrots and has a higher cap, so given a choice between the two you take mesclun. That is a marginal comparison, done crop against crop rather than crop against nothing, and it is the right shape of argument. You also correctly identify the tomato diminishing-returns rate as the reason to hold tomatoes below their cap despite the highest revenue per bed. Three points off for the usual reason: the argument names the rates but never uses them. "10% diminishing returns for tomatoes" is the input; what it does to the cost of the fourteenth bed is the argument. |
| Falsifiability and process | 6 / 20 | "I would know I was wrong because once I build the Excel sheet and run the actual math, I will be able to see the ideal combination of crops to plant based on available resources and costs." That describes what you will do next. It does not name any outcome that would tell you your reasoning was wrong — under that sentence, every possible model result confirms the process. This is the most common failure in the stage and it is the only thing keeping this brief out of the high eighties. |
| **Final** | **80 / 100** | earned on merit |

### How to write the missing section, using what you already wrote

You have made three claims. Each one has a result attached to it that would prove it wrong, and you already know what those results are.

- You claim tomatoes are held to 14 because their 10 percent rate makes further beds too expensive. So: if the model plants more than 14 tomato beds, the penalty is not as punishing as you thought. Decide the band now — is 16 close enough to say you were right? Is 18?

- You claim carrots and mesclun both run to their caps. So: if either comes back below its cap, then something other than the cap stopped it, and your ranking of the three crops was wrong.

- You claim all 64 beds should be used. So: if the model leaves beds empty, then a bed that could be planted is not worth planting, and "use everything you have" is not the right rule.

That is three sentences and it is worth about fourteen points. Write it before you build. A condition written after you have seen the model's answer is not a prediction, and Stage 3 asks you to explain the gap between what you predicted and what the model found — which only works if the prediction was pinned down first.

### A note on your workbook

capabilities/marginal-analysis/model.xlsx exists in your repository and is a single empty sheet, and spec.md next to it is 210 bytes. That is Stage 1.2, due 6 September, and the order matters: the specification is written first and the workbook is built from it, not the other way around.

Committing the skeleton early is fine. Just be aware that a file which exists and a file which is done look identical in GitHub's file list, and the only way to tell is to open it.

---

### How to work this review

Treat this PR the way an analyst treats feedback from a senior reviewer — a review is a proposal to engage with, not a checklist to rubber-stamp.

1. **Read it yourself first.** Form your own view before you change anything. Disagreeing *with a documented reason* is a legitimate, senior response.
2. **Stress-test it with an LLM.** Paste this review and your brief into your assistant and ask it to (a) explain anything you are unsure of, and (b) argue the *other side* — where might the reviewer be wrong, and what would you give up by making each change.
3. **Then write the changes yourself.** For a brief, this matters more than usual: a hypothesis you did not generate cannot be honestly compared against your model in Stage 3, and that comparison is the entire point of writing the brief first.
4. **Close the loop.** Reply in this thread with what you changed and what you pushed back on, then commit and push.

*One standing rule for this stage: do not revise your hypothesis to match what your model later tells you. If the model contradicts the brief, that is a finding, not an error — Stage 3 asks you to explain the gap, and a brief quietly edited to be right afterwards has nothing left to explain.*

— Adam
