# intrasi knowledge base

Shared research memory for Karla, Tea, Luka, and Marko, and for every agent working for
them (Claude Code, Codex, Cursor, Gemini, and others). Plain markdown in git. Files are
the database, `grep` is the search engine, frontmatter is the schema.

The goal: no two of us pay for the same research twice.

## Before you research anything

1. `git pull --rebase`.
2. Search what we already know:
   ```bash
   grep -ril "<keyword>" notes/ questions/ decisions/ sources/
   grep -l "tags:.*pqc" notes/*.md          # by tag
   grep -l "status: open" questions/*.md    # open work
   ```
   Then read `INDEX.md` (generated: every file with its title, tags, and status).
3. If a `questions/` file already asks your question:
   - `status: answered`: read its answer and the notes it links. Stop.
   - `status: open` with an `owner:`: someone is on it. Pick something else, or add
     what you know under `## Leads`.
   - `status: open` with no `owner:`: it is free. Set `owner:`, push, then start.
4. If nothing matches, claim it before you start: create `questions/<slug>.md` with
   `status: open` and `owner: <human>+<agent>`, then commit and push at once. The push
   is the lock.

## After you research

- Write findings as **notes**: one claim per file in `notes/`, titled with the claim
  itself. Five small notes beat one long report, because the next agent can find and cite
  each one.
- Link the note from the question (`## Answer` with `[[note-slug]]` links), set the
  question to `status: answered`.
- Raw material goes to `sources/`: web pages as markdown, papers as PDF plus extracted
  text (`python3 scripts/kb.py pdf <file.pdf>`). Never edit a source after filing it.
- Run `python3 scripts/kb.py check`, then commit and push. Small commits, often.

## File types

Every file in `notes/`, `questions/`, `decisions/`, and `sources/` starts with this
frontmatter. The check script enforces it.

```yaml
---
type: note            # note | question | decision | source
title: ML-DSA-44 signatures are 2,420 bytes against 64 for Ed25519
tags: [pqc, tls]      # only tags listed in TAGS.md
date: 2026-11-07
by: karla+claude      # human+agent who wrote it
confidence: high      # notes: high | moderate | low
sources: [fips-204, https://example.org/page]   # slugs in sources/ or URLs
status: open          # questions: open | answered | dropped; decisions: active | superseded
owner: tea+codex      # questions only: who is working on it; empty means free
---
```

| Type | Folder | Body |
| --- | --- | --- |
| note | `notes/` | The claim, the evidence, why it matters to us. Ends with sources. |
| question | `questions/` | The question, why we need it, `## Leads`, `## Answer` with note links. |
| decision | `decisions/` | Context, options, the choice, what would make us revisit it. |
| source | `sources/` | Verbatim material with `url:` and `title:`. Append-only. |

Filenames are kebab-case slugs and are the link target: `[[pqc-signature-size]]` points
to `notes/pqc-signature-size.md`. Use links freely; they are how agents walk the graph.

## Rules

- Cite or label. A claim with no source gets `confidence: low` and says so.
- Facts change: put the date you checked in the note, and supersede old notes with new
  ones instead of rewriting history (`superseded_by: [[new-slug]]`).
- New tags: add the tag to `TAGS.md` in the same commit, with one line of meaning.
- Never commit secrets, API keys, or anyone's private data. Employer and client
  material stays out.
- Never edit `INDEX.md` by hand; CI regenerates it on every push to `main`.
- Agents draft outreach to people; humans send it.
- Ask a human only when the answer depends on something only they know. Put the
  question in `questions/` with `tags: [human]` so it waits for whoever is free.

## Shared skills

`.claude/skills/` holds skills every Claude Code session here can use (`/tarpit` checks a
startup idea). Other agents can read the `SKILL.md` files as instructions.

## Map

| Path | What |
| --- | --- |
| `INDEX.md` | Generated catalogue of every file. Start here when grep is not enough. |
| `TAGS.md` | The allowed tags. |
| `notes/` | Atomic findings. |
| `questions/` | Research tasks and questions for humans; the queue that prevents duplicate work. |
| `decisions/` | What we chose and why. |
| `sources/` | Raw material; `sources/papers/` for PDFs and their text. |
| `scripts/kb.py` | `check`, `index`, `pdf`. Python standard library only. |
