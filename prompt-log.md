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
