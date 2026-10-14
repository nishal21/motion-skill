# Motion Studio

A code-drawn animation skill. Every frame and the soundtrack are written in deterministic code (`piece.html`, `score.mjs`, `render.mjs`), styled from the references you give it.

## Install

```bash
npx skills add nishal21/motion-skill --skill motion-studio
```

The skill name is `motion-studio`.

| Where | How |
| --- | --- |
| skills.sh | `npx skills add nishal21/motion-skill --skill motion-studio` |
| Cursor | Customize, import `https://github.com/nishal21/motion-skill` |
| cursor.directory | [cursor.directory/plugins/motion](https://cursor.directory/plugins/motion) |
| Claude Code | `/plugin marketplace add nishal21/motion-skill` then `/plugin install motion@motion-skill` |
| Codex | Add this GitHub URL in the plugin browser. The root `plugin.json` is the package. |

## What it does

1. Reads the reference images or clips for palette, texture, line, type, and pacing.
2. Writes a beat sheet: Hook, Build, Breath, Payoff. Default is 15 seconds at 30 fps.
3. Draws the piece in canvas or SVG so `seekTo(t)` always returns the same frame.
4. Renders stills, checks them, then writes a WAV locked to those beats and stitches an MP4.

It does not copy the subjects, poses, or signatures in the references.

## Layout

```
skills/motion-studio/SKILL.md
```

## License

MIT. See [LICENSE](LICENSE).
