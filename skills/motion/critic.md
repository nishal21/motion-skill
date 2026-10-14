# Critic

Score the picture you can see. The timesheet, the style card, and the intent sentence are evidence. They are not the picture.

Write `critic.md` beside the shot. Deliver only when the total is above 8 out of 10. A score of 8 or below is not ready. Fix the weakest category, look again, and score again. After three failed passes, stop and leave the score in `critic.md` with the frame or control that is still wrong.

## How to score

Five categories, each 0, 1, or 2. Add them. The total is the score out of 10.

| Points | Meaning |
| --- | --- |
| 2 | Holds up when you look at the frame or use the control |
| 1 | The idea is there, and one stated fault is visible |
| 0 | Missing, or the fault breaks the read |

Score a category 0 when you have not looked. A storyboard request scores the boards and the timesheet, and skips finished-frame checks by marking them n/a. An n/a category is worth 2 only when the format truly has no such artifact, and you name the skip. Do not mark a failed check n/a to raise the total.

## The five categories

**Intent.** The last frame shows the change the intent sentence names. A UI control ends in the new state. A fight ends on the held result of the hit, not on the windup.

**Timing.** A story pose has a hold. Anticipation comes before a force the audience must see. An action hit is 1 to 3 frames, then a hold. UI entrances decelerate and last longer than the exit. One ease on every element scores 0.

**Read.** The silhouette still reads in one flat color, or the UI change has one leader. The camera does not cross the frame where the idea changes. Twins, a drifting contact, and a mouth that is one drawing all score 0.

**Style.** `style.md` has two cited sources, or a written search failure plus the fallback row. The exposure, impact treatment, camera, and palette density match that card. A copied character, logo, frame, line, or soundtrack scores 0 for the whole shot. The total is then 0.

**Format.** Use the row that matches the job.

| Job | 2 points | 0 points |
| --- | --- | --- |
| UI | `transform` and `opacity`, and a `prefers-reduced-motion` path you tried | Layout properties animating, or no reduced-motion path |
| Anime or cartoon action | Held keys were played first. A smear on the fast gap. An impact frame on contact | Spline with no holds, or no impact on a hit |
| Dialogue | Mouth shapes, each held at least 2 frames. Eyes move before the head | A jaw bob |
| 3D | Constant pose test, then Bézier. Holds are flat. Contacts bookended | Splined before the pose test, or a drifting foot |
| Layout from a script | Poses, holds, and arcs read, and the delivery says layout | Called cleanup |

## `critic.md`

```
Score: n / 10
Ready: yes only when n is greater than 8
Looked at: frame numbers, or the control and the reduced-motion state

Intent: n — one sentence
Timing: n — one sentence
Read: n — one sentence
Style: n — one sentence
Format: n — one sentence

Weakest: the category name, and the frame or control to change
Pass: 1, 2, or 3
```

On a later pass, keep the earlier scores in the file. Do not delete a 6 and replace it with a 9 without saying what changed in the picture.
