# Prompt Log

A running log of meaningful AI-assisted sessions on this repo: what was done, what the AI caught or got wrong, and what I corrected.

## 2026-08-18 — Initial portfolio setup

**What happened:** Used Claude to set up this repo per the course onboarding instructions — converted my rough `BIO`/`BIO.md.txt`/`RESUME.md.txt` drafts into proper `BIO.md` and `RESUME.md`, added `.gitignore`, and created the `.claude/skills/`, `docs/decisions/`, and `docs/templates/` folder structure.

**Errors caught / corrections:**
- Claude's first BIO.md draft ran to 202 words; trimmed it to 193 to stay inside the 150–200 word requirement.
- Fixed a couple of small typos carried over from my original resume text ("Claud" → "Claude", "Hired Score" → "HiredScore" for consistency).
- Claude tried to push its changes directly to GitHub via git and hit a permissions error from Anthropic's side (a known bug blocking pushes from cloud sessions, not a problem with my GitHub setup). Workaround: Claude packaged the files and I uploaded/overwrote them myself through GitHub's web interface.

**Disclosure:** Bio and resume formatting were drafted with Claude's help and reviewed/edited by me before publishing, per the course disclosure requirement.

## 2026-08-18 — Personal LLM foundation setup

**What happened:** Added `AGENTS.md` (with a `CLAUDE.md` pointer), this `prompt-log.md`, a real skill file in `.claude/skills/`, and a first decision memo in `docs/decisions/`, per Step 4 of the onboarding instructions. Also caught that `.gitignore` and the `.claude/` folder hadn't actually made it into the repo from my first upload (likely because dotfiles/dot-folders are hidden by default when dragging files from a folder), and recreated them.

## 2026-08-21 — Fixes and learnings to match Log Stage 0 Compliance instructions
- Asked Claude to vet the repo against the Stage 0 instructions before submitting changes
- AI found README.md was a single heading line, missing the required bio and engagement index
- Four required directories didn't exist: capabilities/, docs/briefs/, data/, analysis/figures/
- First README paste lost all its Markdown — headings, tables, and links came through as plain text and tabs, because it was copied from a rendered view rather than raw source. Fixed by uploading the file instead of pasting.
- Claude first said SKILL.md was fully redundant with AGENTS.md. I pushed back and it was wrong. Tree things were unique/missing. Merged those into AGENTS.md before deleting.
- Claude declined to generate model.xlsx, so I made a skeleton

**Disclosure:** Claude helped me find the right flow of steps

## 2026-08-29 — Stage 1 engagement brief: templates, drafting, and a hostile review

**What happened:** Asked Claude to explain the Perfect Competition case steps and build reusable templates for `docs/templates/` modeled on the professor's own `stage-brief-template.md` and `spec-template.md` from his `shidler` repo. Claude also drafted a fill-in-the-blank scaffold for `docs/briefs/perfect-competition-brief.md`, leaving the problem statement, hypothesis, mechanism, and falsification test blank since those are the graded, student-owned parts. I wrote the actual hypothesis myself, went through two grammar/format passes with Claude, then had it check the brief against the Stage 1 and Deliverable Templates pages before I committed it.

**Errors caught / corrections:**
- My first bed split (12 tomatoes / 28 carrots / 32 mesclun) totaled 72 beds against a 64-bed limit, and put carrots and mesclun both over their per-crop caps. Caught on the first review pass, fixed to 14/20/30, which fits the constraint.
- When I pasted my "final" brief for the commit-format check, it still had the generic template instructions below (the "What is being decided, by whom..." placeholder text) duplicated underneath my real answers. Claude caught the duplication before I committed it.
- Asked Claude to poke holes in the committed hypothesis without rewriting it. It flagged that I never checked whether my labor-hours actually fit the season's labor budget (they do, ~3,210 of 6,480 available hours — I hadn't done that math), that I compared crops by price per bed without netting out labor and fertilizer cost, and that my "how I'd know I was wrong" section doesn't actually state a threshold for being wrong. Also pointed out that since carrots and mesclun are both at their caps in my prediction, 14 tomatoes is partly just arithmetic (64 minus the caps), not fully a test of my P=MC reasoning.

**Disclosure:** Hypothesis, problem statement, and all numbers are mine, written before any modeling, per the case's AI-boundary rule. Claude explained the economics, checked formatting/frontmatter against the Stage 1 and Deliverable Templates pages, and critiqued the committed hypothesis for unsupported claims and falsifiability — it did not write or suggest replacement wording for any of the graded content.
## Stage 2 & 3 — Perfect Competition

**[2026-09-10] — Claude (chat)**
Asked: Review my committed Stage 2 spec for gaps before handing it to a builder.
Got: Flagged that labor-cost formulas were still listed as "pending," and that "near cap" was never defined for the hypothesis test.
Did: Resolved to model temp workers as whole people (not fractional), added `worker_flat_cost` as a named input, and committed the updated spec.

**[2026-09-11] — Claude (chat)**
Asked: Build the Excel workbook from my committed spec.
Got: A three-sheet workbook (Inputs / Labor & Cost / Optimization) with named ranges, plus flags on ambiguities the spec didn't resolve.
Did: Uploaded the workbook to the repo; used it to run Solver.

Asked: Solver kept returning 0/0/0 no matter the starting point — why?
Got: Diagnosis that the flat per-worker cost created a discontinuous profit surface (cost jumps every time a new worker is needed), which GRG Nonlinear can't handle since it assumes smooth gradients.
Did: Switched `temp_labor_cost` to an hourly-variable formula and the Solver method to Evolutionary. Result converged to 10/20/30, matching the case's published check figures, from two different starting points.

Asked: Walk me through Stage 3's four "Learn" questions one at a time.
Got: Guided testing of specific bed counts in my own workbook to derive marginal cost, shadow prices, and the mechanism behind the tomato MC dip, rather than being given the explanations directly.
Did: Wrote all four analysis paragraphs myself from the resulting numbers; built two charts from the data.

Asked: Help me structure the recommendation memo.
Got: The three-part template (plan / judgment call / what would change the answer) and feedback on each draft.
Did: Wrote all three sections myself; tested one hypothesis (whether reordering farmer vs. temp labor priority would change the recommendation) before settling on tomato price as the sensitivity variable.

## 2026-09-11 — Fixed misplaced spec.md path (Stage 2)
- Professor's feedback flagged that capabilities/marginal-analysis/spec.md was a 219-byte stub, and my real spec content was sitting at the wrong path, docs/briefs/perfect-competition-spec.md. I asked Claude for exact easiest steps to fix it.
- Then Claude confirmed that it can see the spec in the correct path.

## Stage 2 & 3 — Perfect Competition

**[2026-09-11] — Claude (chat)**

### Reflection
AI was most helpful for checking calculations, explaining economic concepts, improving the flow of my writing, and formatting the report in GitHub Markdown. It also helped diagnose why Solver was failing after I modeled labor as whole workers instead of fractions, showing that the resulting discontinuous profit surface was causing problems for the GRG Nonlinear method. However, I did not accept every response without verification. AI initially gave an incorrect cell reference while troubleshooting Solver, and I caught the mistake by checking the spreadsheet and noticing that the referenced cell did not exist. AI also helped refine my interpretation of the bed 6 cost dip by showing that the change was caused by the transition from farmer labor to lower-cost temporary labor. To verify results, I checked formulas directly in Excel, reran Solver when outputs looked suspicious, manually confirmed key values such as marginal costs and shadow prices, and tested alternative scenarios. For example, I explored what would happen if temporary labor were hired earlier and found that while profit changed by about $12,500, the recommended crop mix did not, which gave me more confidence in the model's conclusions.

## 2026-09-23 — Brief, Spec, and GitHub Review Setup

**Asked:** Review draft of one-page brief (ask + plan) combining Professor Adam's written
feedback and my original three-question draft, per his format (question, series, what would prove me wrong).
**Got back:** A updated one-pager separating "the ask" (question, concepts,
analysis) from "the plan" (data sources, figures, success criteria), built
around his framing that offshoring and AI are the same cost shock arriving
twice.
**Did with it:** Used this as the base for the brief; pushed back to refine the research
question over several rounds to remove a second, unapproved question folded
into it, per Adam's instruction to pick one question.

**Asked:** Whether a 5-year BLS OEWS window was long enough to detect a break
between the offshoring era and the AI era.
**Got back:** Pushback — 5 years starts mid-COVID and doesn't leave enough
pre-AI baseline to tell a trend break from noise. Suggested 10+ years instead,
backed by a web search confirming BLS OEWS annual data is available well
before that range under a consistent methodology.
**Did with it:** Chose a 10-year window (2016–2025) instead of 5, and
confirmed the job postings series would come from LinkedIn if available.

**Asked:** Review draft of `research-brief.md`, then iterated on wording
across several rounds — replacing "channel" with plainer language, cutting a
policy-tool tangent I didn't want, rewriting the economic-concept bullets in
plain terms, adding a Data Sources section, and standardizing bullet
formatting.
**Got back:** Each revision applied in place, plus an explanation of *why*
"channel" read as jargon and what the plainer alternatives traded off.
**Did with it:** Finalized `research-brief.md` with a single-barreled research
question, plain-language economic concepts, and the three data sources
(BLS OEWS, LinkedIn postings, AI-attribution timeline).

**Asked:** Review draft of `capabilities/economic-research/spec.md` — data sources,
model/figures, and success criteria, including the two-part falsification
test from Adam's feedback.
**Got back:** An updated full spec draft matching the finalized brief.
**Did with it:** Added a "(pending access to data)" note myself on the optional job-postings figure since that data isn't confirmed
yet.
