# Motion examples

Three finished plans. Reuse the timing structure on another subject. Durations are the starting points from [SKILL.md](SKILL.md).

## A button that confirms a save

Format: UI. Tone: product. Setting: a sterile settings screen. Tool: CSS. The motion is one press and one confirm, so it stays a transition.

Intent: the person feels the press land, then sees that the save happened.

Staging: the button is already the focus. Nothing else moves. The label and a check icon are the secondary layer.

Skipped: smear, impact frame, camera, spline, cleanup. A timesheet file is unnecessary. The durations live in the CSS.

| Beat | Time | What changes |
| --- | --- | --- |
| Rest | 0 | Label "Save", scale 1 |
| Press | 0 to 100 ms | Scale to 0.97 with `cubic-bezier(0.3, 0, 1, 1)` |
| Confirm | 100 to 300 ms | Scale back to 1, background to the success token, label to "Saved", decelerate `cubic-bezier(0, 0, 0, 1)` |
| Check | starts at 140 ms, lasts 160 ms | Opacity 0 to 1 and `translateY(4px)` to `0` |

The check starts 40 ms after the confirm, which is the overlap. The scale eases out to 1 and stops.

```css
.save {
  transition: transform 200ms cubic-bezier(0, 0, 0, 1),
    background-color 200ms cubic-bezier(0.2, 0, 0, 1);
}
.save:active {
  transform: scale(0.97);
  transition-duration: 100ms;
  transition-timing-function: cubic-bezier(0.3, 0, 1, 1);
}
.save.is-saved {
  background-color: var(--color-success);
}
.save-check {
  opacity: 0;
  transform: translateY(4px);
  transition: opacity 160ms cubic-bezier(0, 0, 0, 1) 40ms,
    transform 160ms cubic-bezier(0, 0, 0, 1) 40ms;
}
.save.is-saved .save-check {
  opacity: 1;
  transform: none;
}
@media (prefers-reduced-motion: reduce) {
  .save,
  .save:active,
  .save-check {
    transition: opacity 150ms linear, background-color 150ms linear;
    transform: none;
  }
}
```

Add `.is-saved` on release and change the label string to "Saved" in that same moment. The reduced-motion path keeps the color change and drops the scale. If this component already uses GSAP, put the same timings in a tween and branch with `gsap.matchMedia` instead of adding CSS beside it.

## A right cross, TV anime

Format: anime. Tone: action. Setting: shonen clash. Tool: Blender Grease Pencil, 24 fps, shot length 48 frames. Layers: character, effects, background.

Intent: the punch is heavy, and the opponent's head snaps only after the fist arrives.

Staging: both figures stay near the center of the frame. The fist travels on one arc. Empty space sits in front of the punch. Frame 18 jumps to high contrast. By frame 29 the contrast matches the rest of the shot.

| Frames | Exposure | Drawing | What |
| --- | --- | --- | --- |
| 1-8 | hold | A | Guard. Weight on the back foot. Eyes on the opponent |
| 9-16 | twos | B C D E | Anticipation. Rear fist chambers, front shoulder drops, knees bend. The windup points away from the punch |
| 17 | one | F | Smear. The arm is stretched along the arc. The torso has already turned |
| 18 | one | G | Impact, on the effects layer as well as the figure. Cheek flattened, contact mark at full contrast |
| 19-20 | hold G | G | Camera offsets 8 pixels along the punch and stays there. The body drawing stays on G |
| 21-28 | twos | H I J K | Follow-through. The camera eases back. Jacket and hair arrive late. The head lags, then catches the fist |
| 29-48 | hold K | K | The extended fist stays readable. Shoulders take a small breath. Blink on the face layer: half-shut at 40, closed at 41-42, open at 43. The body stays on K |

Playback of A, B, C, D, E, G, and K as held keys comes before drawings F, H, I, and J. If the windup does not read, add frames to 9-16. Do not smooth the smear into a clean in-between.

Mouths are closed the whole shot. There is no dialogue.

## "I waited." in 3D

Format: 3D character. Tone: quiet drama. Setting: a dim kitchen at night, low palette density, one practical light. Tool: Blender armature, 24 fps, frames 1-72. Camera locked, medium close-up, nose room toward screen left, where she looks.

Intent: she is tired of having waited, and the resentment lands on the stressed word "waited".

Audio is already cut. Closed and open shapes hit the track, never after it.

Stepped blocking, Constant interpolation. Play this before any Bézier:

| Frame | Pose |
| --- | --- |
| 1 | Weight even, mouth rest, eyes on camera-left. Hold |
| 10 | Eyes move left. The head has not moved. This is the thought |
| 16 | Head tips down a little. Mouth opens a small shape for "I" |
| 22 | Mouth closes. The word is finished. Face almost still |
| 28 | Accent for "waited". Chin forward, one brow higher than the other, chest drops. Mouth is the wide shape, held |
| 40 | Same face as 28. This second key is what keeps the accent once the curves turn Bézier |
| 48 | Blink. Eyes drop after the blink |
| 64 | Mouth returns to rest. Shoulders settle. A small breath |

The pose test is frames 1, 10, 16, 28, 40, 64. Frame 28, still popping, reads as resentment before any in-betweens exist.

Spline pass, after that test:

- Switch the body curves to Bézier.
- Flatten handles from 28 to 40 so the accent does not melt. Frame 40 exists so a smooth curve cannot eat the hold. Drew Adams's warning is this case: one key at 28 and the next at 64 would have her halfway off the accent by frame 46.
- Keep the eye keys earlier than the head keys.
- Key the head rotation at 28 and again at 29 with the same value.
- Collar and hair start at 32, four frames after the chest drop, and settle at 68.
- Mouth shapes stay at least 2 frames. No extra viseme for the consonants inside "waited" if they crowd the vowel.

FK on the spine and neck, because the arc of the head drop is the performance. IK only if a hand must stay on the counter. Skipped: smear, camera move, impact frame. A moving hold on the shoulders from 64 to 72 is a breath on the same pose.

Light after the pose test. One warm key from screen left, the side she looks toward, so the face separates from the dark cabinets. If the flat-color silhouette of frame 28 fails, fix the pose before you touch the light.
