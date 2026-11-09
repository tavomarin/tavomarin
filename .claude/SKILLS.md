# Vendored Claude skills

`.claude/skills/` holds 697 skills copied from the 20 most-starred Claude skill and plugin
repos on GitHub (ranked by stars on 2026-11-09). Claude Code loads them automatically in any
session opened on this repo, including cloud sessions.

- `skills-manifest.json`: each skill's source repo, the commit it was copied from, and its path upstream.
- `skills-licenses/`: the upstream LICENSE/NOTICE files for each repo. Skills that ship their own
  license (for example the Anthropic ones) keep it in their folder.
- `skills/shared/`: support files that the academic-research skills read through `../shared/`. It is not a skill.

## What was installed

| # | Repo | Skills |
|---|---|---|
| 1 | mattpocock/skills | 31 (the `in-progress/` drafts were left out) |
| 2 | obra/superpowers | 15 |
| 3 | affaan-m/ECC | 314 (only the canonical `skills/`, not the translated or per-agent copies) |
| 4 | multica-ai/andrej-karpathy-skills | 1 |
| 5 | anthropics/skills | 18 |
| 6 | DietrichGebert/ponytail | 6 |
| 7 | nextlevelbuilder/ui-ux-pro-max-skill | 7 |
| 9 | JuliusBrussee/caveman | 22 (skills only, not the proxy) |
| 11 | addyosmani/agent-skills | 25 |
| 12 | Leonxlnx/taste-skill | 1 |
| 13 | tt-a1i/archify | 1 |
| 14 | mvanhorn/last30days-skill | 1 |
| 15 | blader/humanizer | 1 |
| 16 | ayghri/i-have-adhd | 1 |
| 17 | coreyhaines31/marketingskills | 53 |
| 18 | K-Dense-AI/scientific-agent-skills | 177 |
| 19 | Imbad0202/academic-research-skills | 5 |
| 20 | emilkowalski/skills | 18 |

## Not installed

- **#8 Graphify-Labs/graphify**: its skill drives the `graphify` Python package. It does nothing until
  you install that package (`pip install graphify`), which runs third-party code.
- **#10 thedotmack/claude-mem**: its skills talk to the claude-mem background worker and hooks, which
  only exist when it is installed as a plugin (`/plugin install`).
- **anthropics/skills `doc-coauthoring`**: it has no license file, so it isn't redistributed here.

## Changes made to the upstream copies

- **Renamed on name collisions.** When a later repo used a folder name that was already taken, its skill
  got the repo's prefix, both in the folder name and in the frontmatter `name`. Links like `../old/` from
  the same repo were updated to match. Renamed: `uiux-design-system`, `addy-test-driven-development`,
  `science-exa-search`, `academic-deep-research`, `emil-design-eng`, `emil-prototype`.
- **Hook removed from taste-skill.** Its frontmatter defined a `Stop` hook that runs `scripts/gate.mjs`
  every time Claude stops. That hook was removed. You can still run the checker yourself:
  `node .claude/skills/taste-skill/scripts/gate.mjs`.
- Some skills include helper scripts (Python/Node) that Claude runs only when the skill is used.
  They were copied unchanged, so read them before approving a run.

## Things to keep in mind

- **Skills may not be noticed.** Claude Code lists every skill's description in its context but caps the
  space, so with ~700 skills many descriptions get cut short and Claude may not notice a skill on its own.
  You can always call one by name (`/skill-name`). Delete folders you don't use to make the rest easier to find.
- **Updating means re-copying.** These are snapshots. To update, copy the upstream repo again at a newer
  commit (the manifest records the current one).
