# Motion reference

Look this up after [SKILL.md](SKILL.md) has classified the job. Numbers are starting points.

## Principles

Frank Thomas and Ollie Johnston recorded the twelve principles in *The Illusion of Life* (1981). John Lasseter's 1987 SIGGRAPH paper applies them to 3D. Timing, anticipation, staging, follow-through, overlap, exaggeration, and secondary action transfer directly. In a rig, squash becomes scale or a fold, slow-in/slow-out becomes the shape of the F-curve, and arcs are the paths of the bones. UI motion uses the same ideas at a smaller amplitude.

| Principle | Character acting | Interface motion |
| --- | --- | --- |
| Squash and stretch | Volume stays constant. Flesh stretches more than metal. A hinged object folds, as Luxo Jr. does | A press may scale to about 0.97. Skip it when the brand is strict |
| Anticipation | 4 to 8 frames opposite the action. Longer for weight or dread | Usually none. A 2 to 4 px counter-move only on a playful control |
| Staging | One idea, a readable silhouette, room in front of the eyeline | One element moves. The rest hold |
| Straight ahead and pose to pose | Pose to pose for any beat that must land. Straight ahead for fire, water, debris, then retime it | Two states. Pose to pose between them |
| Follow-through and overlap | Cloth and hair start 2 to 6 frames late and stop late | Icon or label starts about 40 ms after the container |
| Slow in and slow out | Drawings cluster at the slow part of the move | Entrance decelerates. Exit accelerates |
| Arcs | Limbs, heads, and props swing on curves | A one-axis move stays on that axis |
| Secondary action | Supports the main idea. It does not start a second performance | Shadow, badge, or underline, on the same idea as the parent |
| Timing | Holds make weight and emotion. A heavy thing is slow to start and slow to stop | Duration grows with the distance traveled |
| Exaggeration | Push the pose until the idea reads, then stop | Stay inside the product's scale. A 4 px move can be the whole idea |
| Solid drawing | Stay on model. In 3D, do not scale the volume away | Sit on the pixel grid. Keep stroke width stable |
| Appeal | A clear line of action through the pose | The motion matches the product's existing tone |

Lasseter's practical test still holds: the audience needs time to catch the preparation, the action, and the reaction. Too little time and the idea is over before it registers. Too much and attention leaves.

## Western 2D pipeline

Order from traditional production (storyboard through photography), with breakdowns called out because that is where arcs are decided:

1. Storyboard. One idea, staging, acting, and camera per shot.
2. Animatic. Boards cut to scratch audio, or to a beat if there is no track yet. Western dialogue is usually recorded before animation. If the track exists, the timesheet follows the track.
3. Layout. Camera field, background, character placement, start pose and end pose.
4. Key poses. The extremes that state each beat.
5. Breakdowns. The bend in the arc and the spacing.
6. Pose test. Play the keys and breakdowns with holds, before in-betweens. Fix the poses here.
7. In-betweens.
8. Second pose test, still before cleanup.
9. Cleanup. Trace a performance that already reads.
10. Color.
11. Composite. Character, effects, and background, then the camera move from the timesheet.

The timesheet (exposure sheet, X-sheet, dope sheet) is one row per frame at 24 fps. Columns that matter: action and holds, dialogue broken into sounds, cel or layer levels, camera (field, pan, truck), effects. A bar sheet joins the same frames to musical beats when the picture is cut to music.

Pencil-test the keys before cleanup. Digital ink and paint replaced cels; the order of the decisions did not change.

## Anime pipeline

1. Storyboard (e-konte): staging, acting, camera.
2. Layout: camera field, background, and where the figure sits from the first frame to the last.
3. Genga: the key drawings. The key animator fills the timesheet's action column as those drawings settle. Play those held keys before in-betweens. A key past the last frame of the shot is legitimate when the motion should still be traveling at the cut.
4. Douga: in-betweens (nakawari) between the keys the sheet names. Spacing marks say whether the gap is even, slow-out, or slow-in. If a spacing mark is missing, keep the gap even until someone marks it.
5. Paint, then composite. Camera pans, shakes, and flashes live on the sheet so photography can run them without redrawing the figure.

Japanese production often records the voice after the picture. If there is no track, put intended phonemes on the sheet as a guide. If a track arrives, move the mouth keys to the track. Closed sounds (M, B, P, F, V) land on the sound's frame or one frame before it. They do not land after it.

Limited animation means longer holds on this same pipeline. TV work often keeps dialogue and body motion on twos and spends ones on the hit. A film shot can stay on ones through the acting. Both still hold the pose that carries the idea.

Draw smears and impact frames by hand. Stroke interpolation between two clean poses will not invent them.

- Smear: 1 to 3 frames, the body stretched along the path so successive positions overlap.
- Impact: 1 to 2 frames, higher contrast, compressed silhouette, its own layer so the flash can be one frame long.
- The strike itself is often a single frame between a long preparation and a longer recovery.

A shake on ones can sit on top of a body that stays on twos. Put the shake in the camera column and leave the figure on twos.

## 3D pipeline

1. Camera and layout in the viewport. Start pose and end pose. Silhouette check in a flat color.
2. Reference, even a rough one: a clip, a mirror, or thumbnails on the timesheet.
3. Stepped blocking. Constant interpolation. Keys, then breakdowns. Mark extremes and breakdowns in the Dope Sheet if that helps you see them.
4. Pose test. Playblast or viewport play. The idea has to read with pops and no in-betweens.
5. Spline. Switch to Bézier. Flatten holds. Break handles on accents. Bookend contacts.
6. Secondary motion and overlap.
7. Polish: anticipation, finger and face detail, a moving hold (a small drift on a pose that must not freeze).
8. Light for separation, then render.

FK when you need to draw the arc: spine, a gesturing arm, the follow-through of a punch. IK when the end must stick: a foot on the floor, a hand on a cup. On the frame you switch, key both the FK chain and the IK influence so the limb does not pop. A walk keeps the legs on IK. Arms usually stay on FK until they plant.

For a grabbed prop, key the Child Of influence from 0 to 1 on the grab frame. Run Set Inverse while the hand is already on the prop. If you set the inverse in the rest pose, the hand jumps on the grab.

### Blender, specifically

Set the scene to 24 fps for film, cartoon, anime, and acting, unless the project rate is already decided.

- Dope Sheet: move, copy, and hold keys. Grease Pencil mode retimes drawings. Interpolated breakdowns show as smaller keys.
- Graph Editor: F-curves. Constant while blocking. Bézier after the pose test. Linear or vector handles for a plant or a snap. Auto Clamped handles are the first spline pass. Then flatten holds and break accents by hand. Continuous Acceleration smoothing can overshoot; if a hold drifts, set the handle smoothing so one key does not reshape the whole curve.
- NLA: stack a blink or a finger action over a finished body action. Do not build the performance in the NLA first.
- Grease Pencil: `File > New > 2D Animation` (onion skin, autokey, camera). Draw the extreme, the breakdown, then the in-betweens. The Interpolate tool makes a breakdown between two similar drawings (a blink, a simple squash). Redraw any smear or impact it produces.
- Layers: character, effects, background. The impact flash is an effects-layer drawing.
- Key types worth using: Extreme, Breakdown, Moving Hold. Jitter keys are baked filler. Do not mark hand-keyed acting as Generated.
- Render a PNG sequence while the timing may still change. Render a movie when the timesheet is locked.

Run the flat-color silhouette test before lighting. If the face fails, move the pose or the camera. Then put the key light on the side the nose points, so the face sits a step lighter or darker than the wall. Add a rim only when the body merges with the ground.

## Exposure at 24 fps

One frame is about 41.7 ms.

| Exposure | Drawings in one second | Use |
| --- | --- | --- |
| Ones | 24 | Fast travel, impact, camera shake, and a film shot drawn on every frame |
| Twos | 12 | Default for TV anime and a lot of cartoon acting |
| Threes | 8 | Slow atmosphere, a near-still, limited holds |

Mix them inside one shot. A held drawing is the same drawing repeated on the sheet. In Grease Pencil the hold is the gap until the next key, unless the exporter needs a duplicated frame.

### Holds to start from

| Event | Starting length |
| --- | --- |
| Story pose the audience must read | 6 to 8 frames; 12 to 16 if it is the point of the shot |
| Mouth shape | At least 2 frames, longer on a stressed vowel |
| Anticipation | 4 to 8 frames; longer for mass or dread |
| Smear | 1 to 3 frames |
| Impact | 1 to 2 frames |
| Overlap offset | 2 to 6 frames behind the leader |

Sprite engines that allow one duration per frame should store those holds. If the engine uses a single frame rate, duplicate the hold frame so it occupies the extra ticks.

### Lip sync

Mouth shapes, grouped the way Preston Blair's chart groups them: rest, closed (M, B, P), wide (AI), E, O, U / W / Q, teeth on the lip (F, V), tongue-up (L). In fast speech, show the vowels and the closings. The head, brow, and chest carry the feeling. Animate the mouth after the body pose is locked. A shape that lasts one frame does not read.

## Interface timing

Material Design 3's easing-and-duration tokens are the starting point for CSS and GSAP. A later Material expressive system uses springs. Use springs only when the project already has a spring library. Otherwise ship durations and curves.

| Role | Duration | Curve |
| --- | --- | --- |
| Tiny state (color, icon swap) | 100 to 150 ms | `cubic-bezier(0.2, 0, 0, 1)` |
| Control press | 100 to 200 ms | accelerate `cubic-bezier(0.3, 0, 1, 1)` |
| Enter the screen | 250 ms, up to 400 ms if it crosses a large area | decelerate `cubic-bezier(0, 0, 0, 1)` |
| Move that begins and ends on screen | 300 ms, up to 500 ms for a large expressive travel | standard `cubic-bezier(0.2, 0, 0, 1)` |
| Exit | about 200 ms | accelerate `cubic-bezier(0.3, 0, 1, 1)` |

In GSAP those decelerate and accelerate roles are `power2.out` and `power2.in` unless the project has already chosen other eases. GSAP's own default ease is `power1.out` and its default duration is 0.5 s. Override both with the duration and curve from the table.

Animate `transform` and `opacity` (GSAP: `x`, `y`, `scale`, `rotation`, `autoAlpha`). Leave `width`, `height`, `top`, and `left` alone unless the layout itself must change. Put `will-change: transform` on the element that animates, and leave it off the page root.

`prefers-reduced-motion: reduce` gets a path you wrote: drop travel and scale, keep an instant state or an opacity change around 150 ms. In GSAP, branch with `gsap.matchMedia` as the gsap-core skill describes. A global rule that forces every duration to 1 ms is a last resort. It misses the Web Animations API, and it can skip work that was waiting on `animationend`.

Use CSS for a single state change and for a short loop of one property, such as a spinner. A sequence of beats, anything you must pause or reverse, and anything tied to scroll, goes to GSAP. Lottie is for a JSON file a designer already exported into a project that has a player. Rive is for a `.riv` file in a project that already runs Rive. Motion (`motion.dev`) is for a file that already imports it. Do not introduce those runtimes for a new button.

## Continuity

Across shots, screen direction stays put. Someone who leaves on frame right enters on frame left. The listener's eyes aim at where the speaker's eyes were. A prop remains in the hand that picked it up, on that side of the body, until a shot shows the handoff. Color of a held object does not shift between shots unless the light source changed and you can point to it.

## Sources

- Frank Thomas and Ollie Johnston, via "Twelve basic principles of animation," Wikipedia. https://en.wikipedia.org/wiki/12_basic_principles_of_animation
- "12 Principles of Animation," Adobe. https://www.adobe.com/creativecloud/animation/discover/principles-of-animation.html
- John Lasseter, "Principles of Traditional Animation Applied to 3D Computer Animation," SIGGRAPH 1987. https://courses.cs.duke.edu/cps124/fall01/resources/p35-lasseter.pdf
- "Traditional animation," Wikipedia. https://en.wikipedia.org/wiki/Traditional_animation
- "About SAKUGA," E-SAKUGA. https://www.esakuga.net/about-sakuga/
- "Timesheet," Anime GO. https://animego.erosakuga.com/benkyou/timesheet/
- "Exposure Sheet (X-Sheet / Timesheet)," Animation Cel. https://animation-cel.com/glossary/exposure-sheet
- Ryan Barone, "What Does Animating on Ones, Twos & Threes Mean?," iD Tech, 2021. https://www.idtech.com/blog/what-does-animating-on-ones-twos-and-threes-mean
- "Frame-by-Frame Anime Animation," Magic Motion Studio. https://magicmotionstudio.com/frame-by-frame-anime-animation/
- jb siraudin, "The visual design of Demon Slayer's combats." https://jbsiraudin.github.io/blog/demon-slayer-visual-grammar
- Drew Adams, "Stepped vs. Spline Blocking in Animation," Animation Mentor, 2018. https://www.animationmentor.com/blog/stepped-vs-spline-blocking-in-animation/
- "Keyframes," Blender Manual. https://docs.blender.org/manual/en/latest/animation/keyframes/introduction.html
- "Animation Editors," Blender Manual. https://docs.blender.org/manual/en/latest/animation/animation_editors.html
- "Grease Pencil Animation Introduction," Blender Manual. https://docs.blender.org/manual/en/latest/grease_pencil/animation/introduction.html
- "Interpolate," Blender Manual (Grease Pencil). https://docs.blender.org/manual/en/latest/grease_pencil/modes/draw/tools/interpolate.html
- "Easing and duration," Material Design 3. https://m3.material.io/styles/motion/easing-and-duration
- "Easing and duration tokens," Material Design 3. https://m3.material.io/styles/motion/easing-and-duration/tokens-specs
- "prefers-reduced-motion," web.dev. https://web.dev/articles/prefers-reduced-motion
- "Lip sync animation: guide and mouth chart," Animperia. https://animperia.com/learn/lip-sync-animation
- Brian Lemay, "Lip Sync Book." http://brianlemay.com/Pages/animationschool/animation/lipsyncbook/lipsync.html
- ahujasid, mcp-for-blender. https://github.com/ahujasid/blender-mcp
- blender-2d-mcp (Grease Pencil, Blender 5.2). https://glama.ai/mcp/servers/Praveen16-V/blender-2d-mcp
- krita-mcp. https://pypi.org/project/krita-mcp/
- tahoma2d-mcp (render an existing .tnz only). https://github.com/sandraschi/tahoma2d-mcp
- "ToonzScript," OpenToonz manual. https://opentoonz.readthedocs.io/en/latest/toonzscript.html
- Tahoma2D. https://tahoma2d.org/
- Krita Scripting School, animation. https://scripting.krita.org/lessons/animation
