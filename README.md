# Motion

An agent skill for animation. It covers interface motion, motion graphics, cartoons, anime, and 3D acting. The agent pulls public references for the style you name, makes a picture the tool can open, then scores that picture. A score of 8 out of 10 or below is not ready.

## Install

skills.sh lists this repo for Cursor, Claude Code, Codex, Copilot, and the other agents that CLI supports. One install is the listing. There is no separate upload form.

```bash
npx skills add nishal21/motion-skill
```

The skill name is `motion`.

| Where | How |
| --- | --- |
| skills.sh | `npx skills add nishal21/motion-skill` |
| Cursor | Customize, import `https://github.com/nishal21/motion-skill` |
| Claude Code | `/plugin marketplace add nishal21/motion-skill` then `/plugin install motion@motion-skill` |
| Codex | The repo root `plugin.json` is the portable plugin. Add the marketplace from this GitHub URL in the Codex plugin browser. |

## What it does

1. Classifies the job: UI, motion graphic, cartoon, anime, 3D, or a hybrid.
2. Writes `style.md` from public sources. It keeps timing, staging, and palette. It does not copy characters, logos, frames, dialogue, or music.
3. Makes the picture. A single UI state is CSS. A sequence or a scroll is GSAP. A drawn or 3D shot goes through Blender when that bridge is connected, or into `shot.py`. Krita is the raster path when its bridge is connected.
4. Scores the picture in `critic.md`. Five checks, each 0, 1, or 2. The agent revises until the total is above 8.

Frame counts in the skill are starting points. The style card overrides them when a cited source gives a different number.

## Layout

```
skills/motion/SKILL.md      procedure
skills/motion/execute.md    bridges and the style card
skills/motion/critic.md     the score
skills/motion/reference.md  principles, pipelines, sources
skills/motion/examples.md   a button, a punch, a line of dialogue
```

## License

MIT. See [LICENSE](LICENSE).
