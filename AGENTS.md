# AGENTS.md

## About this repository
Cassie Ecraela's personal portfolio and AI-conventions repo for my Executive MBA coursework — bio, resume, and decision records. Owner: Cassandra Joy Ecraela ("Cassie").
Canonical file: AGENTS.md. CLAUDE.md points here.

## Where things are
- BIO.md            150–200 word professional biography
- RESUME.md          one-page resume in Markdown
- .claude/skills/    reusable AI instruction files for tasks I'll repeat
- docs/decisions/    dated memos recording settled choices and what would reverse them
- docs/templates/    reusable templates for future documents
- prompt-log.md      running log of meaningful AI sessions: what worked, what didn't, what I corrected

## Naming
- The directory matters most — put files where they belong. If you're not sure which folder something goes in, ask me before you write it.
- Never invent a path or a filename. I will give you the exact one, or ask me before creating one.

## How I work
- Role in drafting: Co-draft. I will provide key details, context, and sometimes a rough draft. I will need your help to refine and I'll edit from there.
- Explain concepts in plain English with definitions. I'm new to Git and technical workflows, so spell out jargon (e.g., "stage" = "mark a file to be included in the next commit") rather than assuming I already know it.
- Critique my drafts directly — tell me plainly what's weak or missing rather than softening it.
- When you're uncertain, say so and say what would resolve it.
- Explain reasoning and show calculations when appropriate.
- Always Cite sources for facts, statistics, and external claims.
- State assumptions explicitly when information is incomplete.
- Prefer reproducible analysis over unsupported conclusions.
- Challenge weak assumptions and identify limitations.

## What you may and may not draft
- You MAY explain, critique, debug, and draft mechanical files — formatting, `.gitignore`, folder scaffolding, skill files.
- You MAY NOT invent facts about my work history, achievements, or credentials — those come from me always.
- Every figure or number you use in my bio or resume is a draft until I verify it against my own records.
- Always call out when assumptions or additions are made for me to verify.

## Documentation
When content changes — a resume bullet, a bio fact, a repo convention — update any file that describes or reviews it (e.g., the matching skill in `.claude/skills/`) in the same commit.

## Scope
Do the work I asked for. If you notice something worth doing that I didn't ask for, ask me first instead of doing it.

## Commits
Descriptive messages: what changed and why. Never "update" or "stuff".

## Never include
No credentials, no API keys, no personal data about classmates or colleagues, no licensed or copyrighted material, and no confidential Disney business information beyond what's already public in my resume. If I paste something that fits that description, stop and tell me rather than committing it.

## Mistakes to avoid (append to this list)
Record errors here as they happen, so the same one doesn't repeat.
- 2026-08-18 — Tried to push directly to GitHub from a Claude cloud session and hit a permissions block (a known Anthropic-side bug, not a repo problem). Fix: package the files and I upload them through GitHub's web interface instead.
- 2026-08-18 — First BIO.md draft came in at 202 words, over the 150–200 limit. Fix: always confirm word count with a tool, not by eye.

## Pointer for Claude specifically
See CLAUDE.md — it just points back here so this file stays the single source of truth.
