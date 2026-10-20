# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->



---

## Label Taxonomy

### `lore_analysis`

**Definition:**
Makes a narrative or world-building argument backed by specific references to game text, timelines, or in-universe history.

**Example 1:**
> **[All] Religions of Hyrule Part 1: Humans**
> This is a post about the religions of Hyrule... The three most important deities of Hyrule are the Three Golden Goddess. Din, Nayru and Farore... Other then the Golden Goddesses, the main deity of the Hylians is the unseen goddess, Hylia, in which the Hylians get their name...

**Example 2:**
> **What is the darkness?????**
> Okay, so the Master Sword is the sword that seals the darkness. At the end of a Link to the Past, Ganon was sealed within darkness... So... can anyone elaborate on what the darkness actually is? Is it the void of the evil realm... or the realm of null beneath the world of light?

### `gameplay_inquiry`

**Definition:**
Asks a direct question or seeks practical troubleshooting help for mechanics, puzzles, or progression bottlenecks while playing a specific game.

**Example 1:**
> **[BOTW] I feel stuck! Help!**
> ...The problem is I don't know what to do now. Any shrines I am still able to find are too difficult for where I'm at in the game. For example, a moderate test of strength - the guardian hits me once and I'm dead. I also have tried to grab a couple more towers, but they are too tall... Anyone willing to give me some advice...

**Example 2:**
> **Lost in LTTP please help**
> Posting here because I took a long break and came back to lttp with no idea what im supposed to be doing... My situation is: I recall beating the wizard at the top of the tower, but when i use my mirror i do not get dark world where I still am Link. I get dark world where i am the Easter Bunny... Hopefully this rings a bell for somebody who can point me to the right track, thanks

### `franchise_discussion`

**Definition:**
Focuses on how the games are built, marketed, or managed by Nintendo (game design philosophy, developer interviews, hardware constraints, release schedules, or series direction) whether positive, neutral, or critical.
>**CHANGED:** Focuses on meta-discussions about the series, the creators, and how the games are made, managed, or marketed. This includes game design choices, developer interviews, hardware constraints, series direction, etc. Any general industry critique whether it's positive, neutral, or critical.

**Example 1:**
> **It's been nearly 15 years since a new, traditional LoZ was released. When do we honestly think the next one will release?**
> "New, traditional LoZ" means: Not a spinoff, Not a remake or HD remaster, Not BotW or TotK given that they... are definitely not "traditional". Traditional formula = a 3D LoZ with the same general, dungeon-focused structured progression as OoT, MM, WW, TP, and SS...

**Example 2:**
> **Is Nintendo really going to sell the same game for each 5 year anniversary from now on?**
> Zelda 25th anniversary - Release of Skyward Sword on the Wii
> Zelda 30th anniversary - Release of Skyward Sword on the Wii U virtual console
> Zelda 35th anniversary - Release of Skyward Sword on the Switch
> Are they gonna keep doing this lol


### The hardest boundary

**Which two labels:**
`lore_analysis` and `franchise_discussion`

**The decision rule I used every time:**
If the post's primary thesis argues about real-world factors, player mechanics, game design philosophy, etc, it is `franchise_discussion`, even if it uses lore elements as examples. If the primary thesis is about explaining chronology, character motivations, or world history, it is `lore_analysis`.



---

## The Dataset

**Where the posts came from:** r/truezelda thread on Reddit.

**How I labelled them:** Either as *cold* or as *pre-labelled – checked*

**Counts per label:**

| Label | Count | Share |
|---|---:|---:|
| lore_analysis | 69 | 34.5% |
| gameplay_inquiry | 69 | 34.5% |
| franchise_discussion | 62 | 31.0% |
| **Total** | **200** | **100%** |

**Three hard cases**

**1.**
> *The post:* [BotW] [TotK] THEORY: the Era of the Wild is getting a third game centered around the triforce.
>
> I know a portion of the fandom is ready to leave the era of the wild, but I had this sudden revelation about the triforce not being in any of the games.
>
> The saga will be a trilogy. A third game about the triforce and how the trilogy fits with the 3 timelines is about to slap us in the face.
>
> OoT Remake was released in the middle of it to reintroduce players to the concept of the triforce, since it hasn't been discussed in a while.
>
> ** doctors break into my room to take me away ** I AM NOT CRAZY, I KNOW WHAT THEY ARE DOING, THE TRILOGY OF THE WILD IS REAL

> *Could have been:* franchise_discussion

> *I chose, because:* lore_analysis
>
> Even though the post touches on community speculation and game remakes, its primary focus is an in-universe theory about the Triforce and how the Wild Era fits into the timeline. Because the core argument revolves around magical lore and timeline structures, lore_analysis is the best fit. Also, the word 'theory' is usually an indicator for talking about the lore of the game.

**2.**
> *The post:*  We've been stuck on the plateau for 8 months!
>
> Seriously, if you're like me and you've watched all the treehouse footage from E3 over and over again, it feels like we have been stuck on the great plateau for 8 months. It's crazy that this one little portion of the game has kept us occupied with things to talk about up until release. I think I'll be completing the shrines, clearing the bokoblin camps, grabbing the chests and killing the minibosses, then I'll be on my way because I want to see something new! I'll probably return to complete the area waaaay later on.

> *Could have been:* gameplay_inquiry

> *I chose, because:* franchise_discussion
>
> Rather than asking for help, the author is discussing hype over pre-release, E3 footage, and community excitement. This player's sentiment and marketing makes franchise_discussion the correct category.

**3.**
> *The post:*
>
>[ALL] There are no port towns in Hyrule.
>
> I recently watched Any Austin's video "Finding the Edge of the World in Zelda" and it made me realize how rare oceans are in this series. Rather ironic considering that it has two games set entirely on the high seas. But in a lot of Zelda games, Hyrule is completely landlocked. And even when there is a coast, there are no port towns.
>
> There have been settlements on the ocean, but most of them are small fishing villages like Papuchia Village, Lurelin Village, and Seesyde Village. You don't see port towns that are trade hubs with large galleons and other sailing ships.
>
> I think it's because the series mostly doesn't care much about what's going on outside of the immediate area the game is set in. Very rarely do you hear people mention other nations or realms beyond Hyrule, it's only if you directly visit other nations in a game that the wider world is given much consideration at all. So, we don't see port towns in Hyrule, because they're inclusion would mean acknowledging that there are places beyond Hyrule for ships to go, and that's just not something that the series thinks about very much.

> *Could have been:* lore_analysis

> *I chose, because:* franchise_discussion
>
> This post critiques how Nintendo designs its game worlds and handles map layouts from a real-world development perspective. Even though, it talks about the port locations, this is mainly a critique.

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:**

**Settings:** <!-- epochs, learning rate, batch size, seed -->

**Anything I changed from the defaults, and why:**

**Split sizes:** <!-- train / val / test, and per-label counts in the test
split. If a label had fewer than about 8 in test, say so — it explains a lot
of next unit's variance. -->



---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:*
- *What came back:*
- *What I changed:*

**Moment 2**

- *What I asked for:*
- *What came back:*
- *What I changed:*

**Pre-labelling disclosure:**

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy |  |  |  |
| Macro F1 |  |  |  |
| F1 — `label_one` |  |  |  |
| F1 — `label_two` |  |  |  |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->



---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted |  |  |  |
|---|---|---|---|
| **** |  |  |  |
| **** |  |  |  |
| **** |  |  |  |

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->



---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** ___ / 30 = ___%

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**2.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**What the pattern in my disagreements tells me:**



---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
