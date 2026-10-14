# Make the picture

The timesheet is not the delivery unless the user asked for a board. Create the shot, then look at it.

A bridge counts only when its tools are listed in this session and the app is open. If a call fails, write the fallback file. Do not say the scene is inside the app.

## Connected bridges

| Job | Bridge | Do this | If it is not connected |
| --- | --- | --- | --- |
| 3D acting or layout | [mcp-for-blender](https://github.com/ahujasid/blender-mcp) `execute_blender_code`, then `look` on frames | 24 fps. Constant keys. Pose test. Then Bézier. Save the blend | Write `shot.py`. Run `blender -b -P shot.py` |
| Drawn cartoon or anime | [blender-2d-mcp](https://glama.ai/mcp/servers/Praveen16-V/blender-2d-mcp) when Blender is 5.2. Otherwise Grease Pencil Python through mcp-for-blender | Extremes, then the smear, then a 1 to 2 frame impact on the effects layer. Look at the impact frame | `shot.py` builds those Grease Pencil strokes and saves a blend |
| Raster frames | [krita-mcp](https://pypi.org/project/krita-mcp/) | Step the timesheet into frames and export a PNG of the held pose. Pressure, warp, and exact raster frames need Linux and Krita 6.0.4. An `unsupported` result stops that call | `A_0001.png` onward, holds duplicated, plus `timesheet.md` |
| A `.tnz` that already exists | [tahoma2d-mcp](https://github.com/sandraschi/tahoma2d-mcp) | Render the frame range, then ffmpeg to a movie | Do not author the scene with this server. Tahoma2D 1.6.1 does not run ToonzScript from it |
| UI | none | Write the CSS or GSAP into the project. Open the page and use the control | The code is the artifact |

Do not drive the Clip Studio clicker bridge. It is pinned to Windows, version 5.1.2, and one UI language, and Celsys does not publish a document API. Hand a PNG sequence and `timesheet.md`.

OpenToonz has no MCP. ToonzScript can place levels that already exist (`scene.setCell`, `scene.save`). Drawings come from the PNG sequence. The manual is [ToonzScript](https://opentoonz.readthedocs.io/en/latest/toonzscript.html).

Maya and Houdini stay the file you were given. Write `maya.cmds` or hython for that file. Do not start a new Houdini scene for a shot Blender can make.

## What a script may claim

Say the level you actually made.

- **Layout.** Solid poses, holds, arcs, and the impact drawing as a graphic shape. A Python stroke can do this.
- **Animatic.** Layout plus scratch timing, sound clicks on the hits, and dialogue stems.
- **Cleanup.** Finished drawings on model. A polyline script is not cleanup. Say so, and leave the keys in the app for the drawing pass.

Look before you deliver. In Blender, use the bridge view on the held pose and on the impact frame. In Krita, export the PNG. For UI, press the control, including `prefers-reduced-motion`.

## Style card

Search before posing. Memory of a show is not a source. Fetch two or three public pages. If the search fails, write that, and use the closest row in the world table in [SKILL.md](SKILL.md).

Write `style.md` beside the shot:

- The style in the user's words
- Two or three sources, title and URL
- Exposure (ones, twos, threes, or milliseconds)
- Anticipation length, and whether impacts exist
- Camera, line or shape, palette density, how large the acting is
- What you refused: characters, logos, traced frames, dialogue, music

When two sources disagree, keep the one that shows frames. The card overrides the world table. The table fills only what the sources never mentioned.

Search the named film, studio, animator, or product, plus the words `animation timing`. For a fight, add `sakuga` or `impact frame`. For UI, add `motion` and `duration`. Use the pages already listed in [reference.md](reference.md) when they match.

Describe the grammar. Do not copy a character, a logo, a frame, a line of dialogue, or a soundtrack.
