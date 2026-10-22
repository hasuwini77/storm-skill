# storm-skill

`/storm` for Claude Code: research a project wide, pick the best 2–5 features, hand the build to `/agt heavy`.

```
/storm                      # 8 lenses, auto-pick, heavy build in a fresh session
/storm 3                    # force 3 picks
/storm quick                # 4 lenses, no adversary, medium build
/storm "monetization"       # bias every lens
/storm --ask                # pause once at the shortlist
/storm --no-build           # research + doc only
/storm --next               # queue the picks for /agt next
```

What runs: 2 Haiku scouts (code only) → 8 Sonnet lenses in parallel (pain, rival, money, native, loop, reach, lever, trust) → judge → 1 Sonnet adversary → auto-pick → `docs/storm/<date>.md` → a new Claude session beside you that types `/agt heavy "…"`.

Needs the [agentille](https://github.com/hasuwini77/agentille) plugin for `/agt` and the `open_sessions` tool. Without Herdr or tmux the skill prints the `/agt` line to paste.

Install:

```
git clone https://github.com/hasuwini77/storm-skill ~/.claude/skill-sources/storm-skill
ln -s ~/.claude/skill-sources/storm-skill ~/.claude/skills/storm
```

Files: `SKILL.md` (the flow), `lenses.md` (the 8 research prompts + schema), `scoring.md` (score, auto-pick, adversary), `handoff.md` (cards, doc template, agt task line).
