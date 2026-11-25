# Top 3 Game Concepts

These are three ideas for a dry, funny 3D first-person game with a New Zealand flavour, built from current news. They're meant to be built with the [`onefile-aaa`](https://github.com/elcronos/whiteout-onefile) skill, which makes a whole 3D game as one HTML file under 2 MB.

*Written 25 November 2026, from a Council review.*

## The three options

1. **[Do Not Feed the Kea](#1-do-not-feed-the-kea-recommended)** *(recommended)*: a ranger with a leaf blower protects stranded campervans from kea and possums at an alpine pass closed by an earthquake.
2. **[Population: 1](#2-population-1)**: the last resident of a small town, after everyone else moves to Australia, keeps the shop, the pub and the petrol pump going while magpies swoop.
3. **[Special Votes](#3-special-votes)**: the overnight count of special votes in a dead-heat election, with loose ballot papers and campaign signs that won't come down.

See also the [comparison](#comparison) and [next steps](#next-steps).

---

## The brief

- **Dry and funny.** The humour is deadpan and official: signs, notices, alerts and radio calls that react calmly to ridiculous situations. There are no zany characters mugging for the camera.
- **Topical.** Each idea uses something in the New Zealand news in November 2026.
- **Appeals beyond New Zealand.** Jokes work on two levels. Wildlife and bureaucracy are funny anywhere, and local place names and details are a bonus for New Zealanders.
- **New Zealand flavour.** Local places, wildlife, sayings and everyday rituals.

## Rules for all three concepts

1. **Never harm native wildlife.** Kea are endangered and much loved, so you can only scare them off, and they come back offended. Introduced pests (possums, rabbits, magpies) are fair game, but nothing gets hurt on screen.
2. **Enemies are animals or objects, never people.**
3. **Keep real names out.** No real politicians, political parties, broadcasters, shop brands or government departments. Use made-up ones like "the Department" and "the Returning Office".
4. **Mock the system, not the people struggling.** Make fun of institutions and the absurdity of the situation, never the people affected by emigration, petrol prices or earthquakes.
5. **Some stories are off limits:** child poverty, the death in police custody, and the school punishment story. The earthquake can be the setting, but no one is shown hurt by it.
6. **The game must fit the skill's limit for a first-person shooter:** one 100 × 60 m map, one weapon, two enemy types, three objectives, three waves and an exit.

## News used (as of 25 Nov 2026)

| Story | Used in |
|---|---|
| A 5.7 earthquake near Arthur's Pass (17 Nov), with aftershocks expected for weeks | #1 |
| A record number of New Zealanders leaving the country, mostly for Australia | #2 |
| Petrol prices pushing up the cost of living (3.2% annual rise) | #2 |
| A knife-edge general election (7 Nov), with neither major party above 30% and final results due 27 Nov | #3 |

---

## 1. DO NOT FEED THE KEA *(recommended)*

> *Kea are protected. You are not.*

**The pitch.** An aftershock has closed the road over an alpine pass. You're the ranger left in charge of the car park, and three tourists' campervans are stuck there. The local kea (cheeky mountain parrots) have noticed that the vans are full of rubber.

| | |
|---|---|
| **Look** | The skill's overcast snow look, the only one it has tested in a finished game, so the lowest-risk choice |
| **Weapon** | A ranger-issue leaf blower |
| **Enemy 1 (flying)** | Kea. You blow them away unharmed; they come back offended. |
| **Enemy 2 (ground, fast)** | Possums. You blow them into trap boxes, and the screen shows *"Predator Free 2050 progress: 0.0001%"*. |
| **Objectives** | Keep all three campervans' wiper blades, rubber seals and roof pods intact for three waves, until the road reopens |
| **Twist** | Aftershock alerts appear on screen without warning, and you have to crouch (Drop, Cover, Hold) or the shaking gets worse. It's funny, and it teaches the real safety drill. |
| **Ending** | *"Road open. The kea have kept the cone."* |

**Why it's first.** It meets all four parts of the brief. Kea really do strip rubber off cars at Arthur's Pass, right where the earthquake struck, and they need no explanation for people outside New Zealand. The news is the setting rather than the punchline, so the game will still be funny after the story fades. And it uses the look the skill renders best.

**Sample signs and messages:**
- *"Do not feed the kea. The kea will feed themselves."*
- *"Campervan 2: wiper blades 1 of 2."*
- *"Aftershock likely. Probably. Please hold."*

**Ready-to-use prompt:**
```
/onefile-aaa Create a first-person shooter. Concept: A deadpan New Zealand comedy at a quake-closed alpine pass car park in aftershock season: armed with a ranger-issue leaf blower, protect three stranded tourists' campervans from kea (flying, non-lethal: blown away, they return offended) and possums (ground, blown into trap boxes) until the highway reopens; aftershock alerts force you to drop, cover and hold. Humour is carried by dry official signage and HUD text. Budget: quick. Directory: ./do-not-feed-the-kea
```

---

## 2. POPULATION: 1

> *Last one out, turn off the lights. Unless it's you. Then leave them on.*

**The pitch.** Everyone in your small town has moved to Australia except you. The welcome sign's population count drops every wave. It's spring, and the magpies are swooping.

| | |
|---|---|
| **Look** | The skill's countryside afternoon look, changed to spring. Not yet tested in a finished game, so a higher visual risk. |
| **Weapon** | A tennis-ball launcher |
| **Enemy 1 (flying)** | Swooping magpies. November is swooping season. |
| **Enemy 2 (ground, fast)** | Rabbits |
| **Objectives** | Keep the town's three essentials running: the corner shop (the "dairy"), the pub, and the petrol pump, whose price goes up every wave |
| **Details** | Farewell banners, a "back in 5 mins" sign that has clearly been there for months, an ice-cream-container helmet as armour, and the pie warmer as health |
| **Ending** | A job offer from Perth arrives. You choose: **Yeah** / **Nah**. |

**Why it's second.** It has the widest appeal. Young people leaving small towns happens all over the world, and Australians know magpie season too. It will stay topical longer than #3. The risks are the untested look and the need to keep it affectionate rather than gloomy, because emigration and petrol prices are real hardships for real families.

**Ready-to-use prompt:**
```
/onefile-aaa Create a first-person shooter. Concept: A deadpan New Zealand comedy in a spring small town whose entire population has moved to Australia except you: armed with a tennis-ball launcher, defend the dairy, the pub and the last petrol pump (its price ticks up every wave) from swooping magpies (flying) and rabbits (ground), non-gory, while the welcome sign's population counter falls; win by keeping all three open. Humour is carried by dry signage and HUD text. Budget: quick. Directory: ./population-1
```

---

## 3. SPECIAL VOTES

> *Every vote counts. Several of them are currently loose.*

**The pitch.** The election is a dead heat. The special votes are being counted overnight in a community hall, the heat pump is broken and blowing hot air everywhere, and the campaign signs refuse to come down.

| | |
|---|---|
| **Look** | Inside a community hall at night, with fluorescent lights and a view of a rainy car park |
| **Weapon** | An official date stamp |
| **Enemy 1 (ground)** | Leftover campaign signs from made-up parties, waddling around on their stakes. Every slogan is a version of *"Getting On With It"*. |
| **Enemy 2 (flying)** | Loose ballot papers blown around by the heat pump. Stamp them and they go back into the right box. |
| **Objectives** | Three tables of ballots, each of which has to be fully counted before the deadline |
| **Ending** | The result is announced: *"Too close to call."* |

**Why it's third.** It's the most topical, but it has the shortest shelf life and the most political risk. Final results come out on 27 November and coalition talks follow, so the news may have moved on by the time the game is ready to share. To stay neutral, every party must be made up and mocked equally.

**Ready-to-use prompt:**
```
/onefile-aaa Create a first-person shooter. Concept: A deadpan New Zealand comedy in a community hall at night during a dead-heat election's special-votes count: armed with an official date stamp, return loose ballots (flying, blown by a broken heat pump) to the right boxes and knock down leftover hoardings from fictional parties (ground, waddling on their stakes, all slogans identical) before the deadline across three counting tables. Humour is carried by dry official signage and HUD text. Budget: quick. Directory: ./special-votes
```

---

## Comparison

| | Kea | Population: 1 | Special Votes |
|---|---|---|---|
| Topical now | ●●● | ●●○ | ●●● |
| Still funny in a year | ●●● | ●●● | ●○○ |
| Appeal outside NZ | ●●● | ●●● | ●●○ |
| NZ flavour | ●●● | ●●● | ●●○ |
| Visual risk with the skill | Low (tested look) | Medium (untested look) | Medium (untested interior) |
| Risk of offending | Low | Medium (emigration is a sore point) | Medium-high (politics) |

## Next steps

1. **Pick one concept.** The recommendation is *Do Not Feed the Kea*.
2. **Write the jokes yourself.** The skill's quality checks only score how the game looks, so nothing in it checks whether the game is funny. Write about 30 lines of signs, messages and radio calls, and add them to the prompt or to the skill's design document (`SPEC.md`) once it's created.
3. **Run it on a machine with a real graphics card,** not in the dev container, with Google Chrome installed. Use `Budget: quick`, which takes about 5 hours and about 4 million tokens.
4. **Test the jokes** on one New Zealander and one non-New Zealander. Have someone fluent check any te reo Māori.

## Sources

- [RNZ: National news](https://www.rnz.co.nz/news/national)
- [RNZ: Election 2026](https://www.rnz.co.nz/news/politics_election-2026)
- [NZ Herald: Afternoon headlines, 25 Nov 2026](https://www.nzherald.co.nz/nz/nz-herald-afternoon-headlines-wednesday-november-25-2026/5O4KVXJIWTNJXHLUUONOWJRP6M/)
- [Democracy Project: News briefing, 25 Nov 2026](https://www.democracyproject.org.nz/p/news-briefing-25-november-2026)
- [Electoral Commission: 2026 preliminary results](https://elections.nz/media-and-news/2026/2026-general-election-preliminary-results)
- [Wikipedia: 2026 New Zealand general election](https://en.wikipedia.org/wiki/2026_New_Zealand_general_election)
- [The Spinoff: Rent is getting cheaper](https://thespinoff.co.nz/business/03-02-2026/rent-is-getting-cheaper-heres-why-thats-not-necessarily-a-good-thing)
- [MPA: Petrol pushes living costs to 3.2%](https://www.mpamag.com/nz/specialty/residential/petrol-pushes-living-costs-to-32-as-mortgage-relief-fades/583897)
