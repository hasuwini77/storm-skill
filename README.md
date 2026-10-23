# storm-skill

`/storm` for Claude Code: research a project wide, pick the best 2–5 features, spec them, then build them.

```
/storm                      # 8 lenses, auto-pick, build
/storm 3                    # force 3 picks
/storm quick                # 4 lenses, no adversary
/storm "monetization"       # bias every lens
/storm --ask                # pause once at the shortlist
/storm --no-build           # research + doc only
/storm --next               # queue the picks for /agt next (agentille only)
```

What runs: 2 Haiku scouts (code only) → 8 Sonnet lenses in parallel (pain, rival, money, native, loop, reach, lever, trust) → judge → 1 Sonnet adversary → auto-pick → `docs/storm/<date>.md`, committed → build.

The build depends on what you have installed:

- **Plain Claude Code:** with tmux live, a new window runs `claude` with a self-contained build prompt. Otherwise the storm session builds with built-in Sonnet subagents: one worktree and one PR per pick, one reviewer pass. It never merges for you.
- **With [agentille](https://github.com/hasuwini77/agentille):** a fresh Claude session opens beside you and runs `/agt heavy "…"` (planner, executors, review fan-out).

Already running agentille? You already have `/storm`, so don't install this too or you'll get two.

Install:

```
git clone https://github.com/hasuwini77/storm-skill ~/.claude/skill-sources/storm-skill
ln -s ~/.claude/skill-sources/storm-skill ~/.claude/skills/storm
```

Optional: `~/.agentille/profile.json` with `name`, `role` and `neverDo` personalises every research prompt. Without it the prompts are generic.

Files: `SKILL.md` (the flow), `lenses.md` (the 8 research prompts + schema), `scoring.md` (score, auto-pick, adversary), `handoff.md` (cards, doc template, build hand-off).

This repo mirrors [`agentille/skills/storm`](https://github.com/hasuwini77/agentille/tree/main/skills/storm). Make changes there; they get copied here.
