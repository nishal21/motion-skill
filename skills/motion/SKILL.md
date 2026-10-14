---
name: motion
description: >-
  Produces professional 2D and 3D animation in any style: UI and web motion,
  motion graphics, cartoons, anime and sakuga, and 3D acting. Use when the
  user asks for animation, motion, a cartoon, anime, UI motion, a style
  reference, Blender MCP, Grease Pencil, Krita, a storyboard, or a finished
  shot. Pulls public references first, then creates the picture through a
  connected Blender or Krita bridge, or by writing CSS, GSAP, or a Blender
  Python file the app can run. Scores the finished picture and revises
  until the score is above 8 out of 10.
---

# Motion

Run this procedure on every animation job. Frame counts and durations here are starting points. Change a number when the intent needs a different read, and write down why.

A shot is one continuous view. Anime paperwork calls that a cut. The timesheet is the frame-by-frame plan (an exposure sheet). Blender's Dope Sheet is the editor where you move keys. Those are different objects.

## 1. Classify

Pick one format:

- UI / web motion
- motion graphic
- 2D cartoon
- anime
- 3D character or scene
- hybrid (name both parts)

Pick a tone: comedy, drama, action, horror, product, or the tone the user named. Write the setting in one line, such as a humid night market, a sterile lab, or a shonen clash.

Write one intent sentence: who watches, what they should feel, and what is different on the last frame. If you cannot write it, ask before you pose anything.

A storyboard or animatic request stops after staging and the timesheet. Do not draw in-betweens for a board.

## 2. Pull the style

Search before you pose. Write `style.md` with two or three public sources, the exposure, the anticipation, whether impacts exist, the camera, and the palette. The steps and the refusal list are in [execute.md](execute.md).

A style you remember and cannot cite does not go on the card. If the search fails, say so and use the closest row in section 5. The card overrides that row where both speak.

Do not copy a character, a logo, a frame, dialogue, or music. Take the timing and the staging.

## 3. Make the picture

Match the deliverable. Use the default. Take the escape only for the reason in that row. Then create the artifact in [execute.md](execute.md). A timesheet alone is a board, not a shot.

| Deliverable | Default | Escape |
| --- | --- | --- |
| One UI state: hover, press, color, a small move | CSS transition on `transform` and `opacity`, written into the project | That component already animates with GSAP or Motion |
| A sequence, a scroll, or motion the user can interrupt | GSAP. Read the gsap-core skill before writing a tween. Scroll uses the gsap-scrolltrigger skill | The file already imports Motion (`motion.dev`), a Lottie player, or a Rive runtime |
| A rendered motion-graphic or explainer video, or any project that already has HyperFrames compositions | The hyperframes skill owns the HTML contract and the render. Carry this skill's timesheet into it | The user named a different video framework |
| A cartoon, anime, or 3D shot that must be rendered | Blender at 24 fps, driven by the connected Blender bridge. Grease Pencil for drawn 2D. An armature for 3D. If no bridge is connected, write `shot.py` | The shot already lives in Maya or Houdini. Krita MCP for raster frames. Tahoma2D only to render a `.tnz` that already exists |
| A vector illustration on a page | SVG animated with CSS or GSAP | A Lottie or Rive player is already loaded |
| A sprite or frame sequence | Timesheet first, then frames exported in order | The game already has a sprite pipeline |

Maya is this same blocking-to-spline procedure under other editor names. Houdini stays the DCC when the scene is already a Houdini file. Do not open a new Houdini scene for a shot Blender can render. Do not add a second animation library beside one the project already uses. Do not drive the Clip Studio clicker bridge.

Name the level you delivered: layout, animatic, or cleanup. A scripted stroke is layout until someone draws it on model.

## 4. Build in this order

Skip a step only when the format has no such artifact, and name the skip when you deliver. Order: intent, staging, timesheet, key poses, breakdowns, in-betweens, secondary motion, polish, readability.

### Intent

Use the sentence from section 1. Keep a pose, a hold, or a UI state only when it serves that sentence.

### Staging

One idea in the shot. Place it where the eye already is. Fill the character with one flat color: if the attitude disappears, the pose fails. Leave space on the side the eyes look toward.

If a camera move crosses the frame during the action, start the move after the action has landed, or delete the move. UI staging is the layout. One element carries the change. The rest hold, or they follow by the overlap offset in the secondary step.

### Timesheet

Write it before in-betweens. Film, cartoon, anime, and 3D acting use 24 fps unless the project is already another rate. UI uses milliseconds.

Each beat names the frame, the pose, and the hold.

- A story pose starts at a 6 to 8 frame hold. If that pose is the point of the shot, try 12 to 16 before you add in-betweens.
- A mouth shape stays at least 2 frames.
- Anticipation before a force the audience must see starts at 4 to 8 frames. Add frames for a heavy body or a horror delay. Use fewer frames for a comedy snap.
- A smear on a fast travel is 1 to 3 frames. An impact drawing is 1 to 2 frames.
- UI control changes start at 100 to 200 ms. A panel entering the screen starts at 250 ms and leaves in about 200 ms. A move that stays on screen starts at 300 ms. Longer travel can go to 400 or 500 ms. Past that, the user is waiting.

Curves, ones/twos/threes, and the easing values are in [reference.md](reference.md).

For a blend file or a frame sequence, leave the timesheet in the project (a text block in the scene, or `timesheet.md` beside the file). A UI change keeps its durations in the code.

### Key poses

Extremes only. In Blender, set those keys to Constant interpolation so each pose holds until the next key. Play them. If a beat is unclear with no in-betweens, change the pose.

Each key pose changes the silhouette. Put the weight on one leg. Let one arm lead. Use a symmetrical pose for a formal bow, a mechanical cycle, or a graphic icon.

Emotion is chosen before the travel. Eyes move before the head. The head moves before the torso, unless the body leads (a punch, a flinch). A blink sits on a change of thought. A blink on the stressed syllable hides the accent.

### Breakdowns and arcs

The breakdown is the pose where the path bends. Limbs, heads, and swinging props travel on arcs. Cluster drawings where the motion slows. Spread them where it speeds up.

A UI element moving on one axis stays on that axis. An arc on a button slide is an accident.

### In-betweens and easing

Drawn work waits until keys and breakdowns have been played. Default anime and limited cartoon acting to twos: each drawing held 2 frames at 24 fps. Switch to ones on a hit, a smear, or a camera shake. Use threes on a slow atmospheric move or a near-still. A camera shake can run on ones while the body stays on twos.

3D stays on Constant keys until that pose test reads. Then switch to Bézier. In the Graph Editor, flatten the handles across a hold so the value stays put. A pose meant to hold for 24 frames, keyed once and then eased toward a later pose, is halfway gone by frame 12. Put a second key, with the same value, at the end of the hold. Break handles where the direction turns. Key a foot or hand contact, then key the same value one frame later so the contact does not drift. Use a linear segment on a foot plant or a mechanical snap. A gesturing arm stays on an eased arc.

UI eases by role. An entrance decelerates and lasts longer than the exit. An exit accelerates. The curves are in [reference.md](reference.md).

### Secondary motion

Start cloth, hair, a tail, a dangling prop, or a UI label after the leader. Starting offset: 2 to 6 frames at 24 fps, or about 40 ms in UI. Let it continue after the leader stops. The late start is overlap. The late stop is follow-through. Secondary motion carries the same idea as the body. A coat that flails during a still line is a second performance.

### Polish

Add anticipation opposite the coming action: a crouch before a jump, a chambered fist before a punch, a 2 to 4 pixel counter-move before a playful control settles.

Anime and cartoon action gets a smear on the fast gap and an impact frame at contact. The impact frame is higher contrast, the silhouette compresses, and the camera may bump one or two frames along the hit. Leave smears and impact frames off dialogue and off UI.

Squash and stretch keep volume. A shape that flattens gets wider. In 3D, a scale-down on one axis gets a compensating scale on the others. Rigid metal stretches less than flesh. A hinged object squashes by folding.

Cleanup, color, and lighting come after the pose test.

### Readability

Run the checklist in section 6.

## 5. Retune the world

Keep the steps in section 4. The style card wins where it names a number. This table fills the rest. Change timing, posing, camera, and palette density. Palette density means how many hues are in the frame and how hard the subject separates from the ground.

| World | Timing | Posing | Camera | Palette density |
| --- | --- | --- | --- | --- |
| Humid night market | Settles run long. Cloth and steam arrive after the body stops | Weight sits low. Glances cut across the crowd | The camera barely moves. Cuts follow eyelines | Many warm pools, large dark gaps |
| Sterile lab | Short moves that finish on a chosen frame. Little overlap | Upright, small hands, the gesture ends where it aimed | Locked, or one slow push. Action stays centered | Few hues. Subject separates from the ground |
| Shonen clash | Windup of 8 or more frames, strike in 1 to 3, then a held impact | Extreme line of action, large empty space around the hit | Punch in on contact. Shake on ones, only on the hit | High contrast. The impact frame blows out or drops to a silhouette |
| Comedy short | Hold the take. Leave faster than you arrived | The silhouette changes on the joke frame | Cut. The camera stays out of the gag | Flat, few shapes, easy to read |
| Quiet drama | Holds outlast the line. Eyes move before the body | Small weight shifts. The face does the sentence | Still, with room in front of the eyeline | Low contrast, one accent |
| Horror | The windup lasts past comfort. The stop comes early or late | The pose stops short of the expected target, or overshoots it, then holds | Still, until the move itself is the scare | A dark field and one hard highlight |
| Product UI | 100 to 200 ms on a control, 250 to 400 ms on a panel. Bounce only on a small element in a playful brand | The layout is the pose. One element leads | No camera | The product's existing color tokens |

A setting that is not in the table borrows the closest row. A hybrid uses the character row for the body and the product row for the interface around it.

## 6. Quality bar

Fix every hit that applies to this format. Name any item you skip. A button skips mouths, smears, and spline. A dialogue shot skips impact frames.

- [ ] The intent sentence exists, and the last frame shows the change it names.
- [ ] Stepped or held keys were played before any smoothing.
- [ ] A story pose has a hold. The idea does not start and end on the same frame.
- [ ] The silhouette still reads in one flat color.
- [ ] Limbs, heads, and swinging props travel on arcs. A one-axis UI move is straight on purpose.
- [ ] Check for twins (both arms doing the same thing). Symmetry is reserved for a bow, a mechanical cycle, or an icon.
- [ ] Feet, hands, and a landing cursor do not drift through the hold.
- [ ] Mouths use shapes (closed, wide, narrow, teeth on the lip), each held at least 2 frames. A jaw bob with one mouth drawing fails.
- [ ] Cloth, hair, or a trailing UI label starts late and stops late.
- [ ] An action shot has anticipation before the strike and an impact frame on contact. A quiet shot has no smears and no impact frames.
- [ ] 3D was splined after the pose test. Holds are flat in the Graph Editor.
- [ ] The camera does not travel across the frame where the idea changes.
- [ ] Screen direction matches the surrounding shots. A prop stays in the hand that took it.
- [ ] UI animates `transform` and `opacity`. `width`, `height`, `top`, and `left` stay still unless the layout change is the point and you accepted the cost.
- [ ] UI honors `prefers-reduced-motion`: travel becomes a short opacity change or an instant state. GSAP uses `gsap.matchMedia`.
- [ ] Entrances decelerate. Exits accelerate and are shorter. One ease on every element fails.
- [ ] A looping clip shares pose and velocity on the first and last frames.
- [ ] Squash does not change the volume.
- [ ] `style.md` names two sources with URLs, or it says the search failed.
- [ ] The picture exists: code in the project, frames in the open app, or `shot.py` plus the blend or PNG sequence. You looked at the held pose and, on an action shot, the impact frame.
- [ ] The delivery names layout, animatic, or cleanup, and it matches what you can see.

## 7. Score it

Run [critic.md](critic.md) on the picture you looked at. Write `critic.md` beside the shot. Five categories, each 0, 1, or 2. The total is out of 10.

A score of 8 or below is not ready. Fix the weakest category, look again, and score again. Hand the work over only when the score is above 8. After three failed passes, stop and leave the score with the frame or control that is still wrong.

## 8. What to hand back

| Ask | Produce | Leave out |
| --- | --- | --- |
| Animate this button | The CSS in the project, a reduced-motion path, and a look at the control | A film timesheet |
| Sequence these sections on scroll | A GSAP timeline, after gsap-core and gsap-scrolltrigger | A second animation library |
| A motion-graphic or explainer video | `style.md`, a timesheet, then the hyperframes skill | A second composition runtime, and a Blender scene unless the user asked for 3D footage |
| An anime fight beat | `style.md`, the timesheet, then Grease Pencil keys in Blender or `shot.py`, including the smear and the impact | Spline-only motion with no held drawings, and a claim of cleanup from a script |
| A cartoon short | `style.md`, boards, animatic timing, then keys after the pose test | In-betweens drawn before the pose test |
| A 3D acting shot | Stepped blocking in the blend or `shot.py`, then a spline pass after the pose test | A render of the first spline |
| A sprite attack | A frame list with per-frame holds, files exported in order | One duration shared by every frame |
| A storyboard only | Boards, `style.md`, and a timesheet | Finished frames |

Every row also leaves `critic.md`. Omit it only when the user asked for a score-free sketch and said so.

## 9. Look up the rest

How to search, which bridge to call, and what a script is allowed to claim: [execute.md](execute.md).

How to score, and the pass line above 8: [critic.md](critic.md).

Principles, pipeline order, timing numbers, Blender editors, and sources: [reference.md](reference.md).

A button, a 48-frame punch, and a 3D line of dialogue: [examples.md](examples.md).

When you write GSAP, the gsap skills own the API. When the deliverable is a HyperFrames composition, the hyperframes skill owns the composition. This skill still decides the acting and the timing.
