# intrasi-kb

Our shared research memory. Agents read [AGENTS.md](AGENTS.md) (Claude Code reads it
through `CLAUDE.md`). Humans need three habits:

1. Start every agent session inside this repo, or point the agent at it.
2. Before asking an agent to research, tell it: "check the KB first".
3. Let it push small commits to `main` (`git pull --rebase` first).

Catalogue: [INDEX.md](INDEX.md). Open work: `grep -l "status: open" questions/*.md`.
