# Do Not Feed the Kea v2: KEA mode

The sequel prompt for [Do Not Feed the Kea](https://github.com/cgbarlow/kea-game) ([play v1](https://kea.chrisbarlow.nz/)):
the same car park, played as the kea. Drafted on 27 November 2026 by a Council review run with
[Campaign Mode](https://github.com/cgbarlow/campaign-mode), from this repo's brief and rules and the finished v1 build.

Unlike the three original prompts, this one is not a fresh `/onefile-aaa` run. The skill only starts new projects, so
v2 is built on top of the v1 code: run the build prompt in Claude Code from a clone of
[kea-game](https://github.com/cgbarlow/kea-game), with the `onefile-aaa` skill installed for its tools, critic and gates.

## One-line concept (html-game-concept style)

> *The kea are protected. The cone is not.*

```
A deadpan New Zealand comedy, the same quake-closed alpine pass car park from the other side: play as a kea (first-person, hop, flap and glide), strip rubber from three stranded campervans and steal the Department's road cone before the highway reopens, while the ranger tries to blow you away with the leaf blower (you tumble, you return offended, faster and stronger) and possums compete for the vans; when an aftershock alert sounds, the ranger has to drop, cover and hold, so that's your window. Humour is carried by dry official notices addressed to the kea, who ignores them.
```

## Build prompt

```
Build v2 of DO NOT FEED THE KEA in this repo: enable the KEA entry in the title-screen mode selector and make it a
complete, playable mode. Ranger mode (v1) must keep working exactly as it does now.

Do not re-scaffold. This is an increment on the v1 code. Use the onefile-aaa skill (~/.claude/skills/onefile-aaa) for
its process and tools only: the cookbook rules in src/cookbook/CONTRACT.md, tools/capture.mjs, tools/bench.mjs,
tools/playtest.mjs, the blind onefile-critic subagent and the gates in references/. Use agents for the module work.
Start by adding a "v2: KEA MODE" section to SPEC.md and the new modules to OWNERS.md, then build.

CONCEPT
The same car park, the same 7-minute shift, seen from the kea. You are one kea. The Department of Pass Conservation's
notices, HUD toasts and signs now address you directly, in the same deadpan voice, and you ignore all of them.
Tagline: "The kea are protected. The cone is not."

RULES (from html-game-concept, still binding)
- Nothing is harmed. When the kea is blown away it tumbles, rights itself and comes back offended. There's no death,
  blood or injury, and the tourists are never hurt or frightened, only mildly inconvenienced.
- The ranger is not an enemy to defeat. You cannot attack or damage the ranger. The ranger is doing their job; the
  joke is on the Department's procedures, not on the person.
- No real organisations or brands. Keep "the Department".

PLAYER (first person, kea eye height about 0.35 m on the ground)
- Ground: walk/hop (WASD), with a slight head-bob that reads as hopping, not walking.
- Flight: Space flaps to climb (limited by a stamina meter that recovers on the ground or perched), and releasing it
  glides. Arcade flight: no stalls, auto-level, a capped climb rate and a 14 m ceiling so the view and the perf
  budget stay bounded. Land automatically when slow and close above a surface: van roofs, cabs, mirrors, signs, the
  gate arm, picnic tables, lamp heads, the shelter roof. Mouse looks, gamepad works, pointer lock as in v1.
- View model (the new hero object, replacing the blower): the kea's own beak at the bottom of the frame (olive
  upper mandible, long curved hook, grey cere) and the wing leading edges with orange underwing flashes on every
  flap. Reuse the v1 kea textures and feather materials (src/modules/kea) so it matches the AI kea.
- PULL (LMB hold): grip a part (wiper blade, door seal, mirror, roof-pod strap) and tug. A progress ring fills while
  the beak wiggles it free; the van's integrity drops as in v1. The part then hangs from the beak and can be carried.
- CARRY: fly a part to the kea stash (a rock ledge on the north scree, clearly marked by a growing pile) to bank it.
  Carrying something big (the cone) halves climb rate.
- SQUAWK (RMB): a loud call. It pulls the ranger's attention towards the sound for 3 s (a decoy when you squawk from
  a perch away from your target) and has a 6 s cooldown.

OPPOSITION
- The ranger: an AI character using the v1 leaf blower (same model, third-person), the same force cone and tumble
  physics, now applied to the player kea. Procedural human figure in Department hi-vis and a beanie, readable at
  distance, never close-up on the face. Patrols the vans, reacts to pulling noise and squawks, prioritises a possum
  at a van door over you, overheats the blower (v1 rule), and in an aftershock drops, covers and holds (crouched,
  not blowing) for the whole shake. Getting blown away: tumble, then you return OFFENDED: +speed and +pull strength,
  stacking 3 times (v1's "return offended, faster, harder", now as the player's comeback mechanic).
- Possums: reuse v1 possums. They head for the van doors as before; a possum inside a van locks that van (no more
  pulling) until the ranger traps it. They are rivals, and a distraction you can use.
- Aftershocks: the same five alerts and shakes. The HUD still tells the kea to drop, cover and hold. The kea is not
  required to. The ranger is, and that's your window.

OBJECTIVES AND END
- Bank a quota of rubber parts at the stash (tune so a good run needs most of the shift), and steal the Department's
  road cone from the ROAD CLOSED gate and bank it too.
- Win: quota and cone banked before the highway reopens. End line: "Road open. The kea have kept the cone."
- Lose: the highway reopens first ("Road open. The kea have not kept the cone. Yet."), or three Department notices
  (each time you are blown off a van mid-pull with a part still attached = one notice): "You have been relocated to a
  quieter car park. You will find your way back."
- End screen stats in departmental voice: parts recovered, cone status, notices received, times offended.

HUD AND COPY (Department voice addressed to the kea; write about 30 lines, examples:)
- "Notice to kea: this is not your car park."
- "Wiper blade removed. The Department has noted this."
- "Aftershock alert. Drop, cover and hold. This applies to kea. It does not apply to kea."
- "Kea offended (2). Offence has been logged."
- Stash counter as "Items held for research: 4 of 9". Stamina as "Wing capacity".
- Title-screen note for KEA changes from "Pending risk assessment" to "Risk assessment complete. Risk confirmed."

ENGINEERING
- Mode is data-driven: enable the existing KEA entry in the modes list, branch on G.mode ('ranger' | 'kea') in
  main.js. Share the world, vans, terrain, possums, audio, weather and post. New modules: keaplayer (controller, view
  model, verbs), ranger (AI character), keagame (rules, director, end states), plus kea-mode HUD panels. AI kea from
  v1 stay as background flock (2-3 birds, non-player) in kea mode.
- Harness: ?mode=kea starts kea mode directly; ?shot and #bench work in both modes.
- 6 new kea-mode hero poses (record them in SPEC.md): on a van cab mid-pull with the ranger turning; gliding down the
  car park into the sun, beak in frame; perched on the ROAD CLOSED gate arm eyeing the cone; carrying the cone over
  the vans; the stash ledge with the pile and the car park below; the ranger crouched in an aftershock as a kea lands.

GATES (both modes, same build)
- G1: both modes boot, 6 ranger poses + 6 kea poses capture with 0 errors.
- G2: the blind critic on the 6 kea poses, the skill's own bar (references/quality-bar.json); 2 critic rounds.
- G3: the playtest bot reaches win and lose in BOTH modes, exercises every kea verb (hop, flap, glide, land, pull,
  carry, squawk) and gets blown and returns offended, 0 console errors over 5 min. Ranger mode must still pass its
  v1 script unchanged.
- G4: perf must not regress. Auto quality holds 60 fps at 1920x1080 on the base M4 Mac mini in both modes (bench the
  kea mode with a fly path at 0.3-14 m). Never ship a G4 failure.
- Size: single dist/index.html < 2 MB, no binary blobs.

SHIP
- Update README (kea mode section, controls, 2 new screenshots), bump to v2.0.0, rebuild index.html, commit on a
  branch v2-kea-mode and tell me when it's ready to play; I'll decide when to merge, push and release.
```
