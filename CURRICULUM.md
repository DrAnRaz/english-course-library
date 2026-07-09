# English Course Library — Locked Curriculum Spec (v2, 2026-07-08)

**Author:** Dr. Anikó Rasztovácz · Built 2026-07-07
**Audience:** Kids & teens ~9–15 · One-to-one online lessons over **Zoom**
**Design:** Neurodivergent-first (ADHD/autism/dyslexia-friendly)
**Levels:** 0–6 mapped to CEFR: 0=pre-A1 · 1=A1 · 2=A2 · 3=B1 · 4=B2 · 5=C1 · 6=C2
**Live site:** https://dranraz.github.io/english-course-library/

---

## Session template (ALL 70 sessions — non-negotiable ritual)

Every session is ONE self-contained HTML file (no external resources, offline-capable) with the same 8-step structure and continuous step numbering:

| Step | Block | Core time |
|------|-------|-----------|
| 1 | 🎯 Hello & Today's Goal (one-sentence goal, student says it back) | 2 min |
| 2 | ⚡ Warm-Up (talking/moving game, no score) | 5 min |
| 3 | 📝 New Words (vocab cards with 🔊 click-to-hear + self-check quiz) | 10 min |
| 4 | 📖 Reading & Listening (chunked text with 🔊 Listen + comprehension quiz + open questions) | 10 min |
| 5 | 🔧 Grammar / Language Focus (visual rule box + self-check quiz) | 10 min |
| — | 🤸 MOVE! break card (30–60 sec physical break, always between Step 5 and 6) | 1 min |
| 6 | 🎨 Creative Task (make/write/present something personal) | 10 min |
| 7 | 🎮 Challenge Game (embedded game round: hardest material, score + stars) | 8 min |
| 8 | 🏁 Review & Homework (recap + small creative homework + self-evaluation) | 3 min |

**Honest timing:** per-step timings live in the colored headers but are **teacher-mode only** (student view never shows minutes or "≈50 min core" — the header badge names the goal only). Steps 4, 6, 7 each carry a marked "⏭ SKIP-IF-SHORT" sub-part so a 45-min lesson always ends cleanly.

### v2 additions (2026-07-08 — teacher/student view split + pedagogy hardening)
- **Teacher-view gating (CSS, engine-level):** `.timing` chips and `.zoom-cue` lines are `display:none` by default and revealed only under `body.teacher-mode`. Header badge carries NO minute count.
- **Step-1 goal split:** student view = ONE short kid-language goal line (≤12 words, no "You will learn" meta, no spoiling the Step-5 grammar reveal). The full spoken goal script lives in the Step-1 teacher note as **Say:** "…".
- **Noticing cue:** every non-review session's Step 4 opens with a student-facing hint: `🔎 Watch for [target form] in the story — we unlock it in Step 5!` (legitimizes the encounter-before-explain design).
- **Homework loop:** every session N≥2 Step-1 teacher note STARTS with `Homework check (S{N-1}): …` — the assign→check→build chain must never break.
- **Teacher note per step = 8/8:** Step 3 (New words) and Step 8 (Review) must each carry a `.teacher-note.t-only` like every other step (Step 8's is in addition to the self-eval `.t-only` form).
- **Gender-neutral teacher cues:** zoom-cues and teacher notes always say "the student … they/their". Reading characters keep their genders.
- **Reading lengths (v2 = v1 +40%):** L0 ~65–85 words · L1 ~140–190 · L2 ~290–360 · L3 ~350–440 · L4 ~480–520 · L5 ~600–760 · L6 ~690–760. Readings stay chunked (≤3-sentence paragraphs, mini-subheads).
- **Zoom delivery (see TEACHER_GUIDE §2):** default = "student drives" (student opens the live URL on their own device and shares their screen; teacher keeps a private teacher-mode window). Fallback = dual-window share (share only the clean student-view window).

### Required mechanics (identical engine in every file)
- **Student name field** at top → localStorage → used in encouragements + save filename. NO hard-coded student names.
- **Visual agenda** at top: 8 steps as checkable pills; checking gives progress feel.
- **TTS audio**: `say(text)` via speechSynthesis (en-GB, rate 0.9). 🔊 on every vocab card, reading text, and key example sentences. THIS IS MANDATORY at every level.
- **Self-check quiz engine** (`buildQuiz`): instant kind feedback ("Almost! The green one is right 💪"), score bar, ⭐–⭐⭐⭐ stars at 50/80%.
- **Auto-save**: debounced localStorage, key prefix `ecl_L{level}s{session}_`. "💾 Save my work" exports .txt named `{StudentName}_L{level}S{session}_{date}.txt`.
- **Teacher mode**: 🔐 button, PIN `teach` → reveals `.t-only` blocks (teacher notes per step, ANSWER KEYS — keys are NEVER visible in student view, self-eval checklist).
- **Zoom cue**: every step header has a small `📹` chip: the Zoom mechanic (e.g. "Student annotates on your shared screen", "Use 👍/👎 reactions", "Drop game link in chat", "Student shares her screen").
- **ND accessibility**: body ≥16px; readings chunked into ≤3-sentence paragraphs with mini-subheads, never italic, max ~65ch; color + icon + TEXT triple coding (never color alone); high contrast; one continuous step numbering; predictable block order; encouraging, literal language (no idioms in instructions below L4).

---

## Curriculum map — 70 sessions

### Level 0 — No Proficiency (pre-A1) `Level_0_No_Proficiency/`
Formulaic chunks, massive visuals/emoji, TPR (move, point, show), instructions dual-language friendly (very simple English + 🔊 everywhere). Readings = short picture-supported lines, ~65–85 words (v2).
| # | Title | Focus |
|---|-------|-------|
| 1 | Hello! | Greetings, "Hi, I'm ___", How are you? |
| 2 | ABC & My Name | Alphabet, letter sounds, spelling your name |
| 3 | Numbers & Age | 1–20, "I am ___ years old", counting games |
| 4 | Colors & Shapes | 11 colors, 5 shapes, "It's a red circle" |
| 5 | My Family | mum/dad/brother/sister/grandma/grandpa, "This is my ___" |
| 6 | My Body | Head–toes, Simon Says, "Touch your ___" |
| 7 | Animals | 12 pets & farm animals, "It's a ___", animal sounds |
| 8 | Food I Eat | 12 basic foods, "I like ___ / yum/yuck" |
| 9 | My Things | School objects, "This is my ___", in my bag |
| 10 | Review Party 🎉 | Cumulative games, mini-certificate |

### Level 1 — Beginner (A1) `Level_1_Beginner/`
Sessions 1–3 are UPGRADED ADAPTATIONS of the Dea course S1–S3 (same topics/grammar, de-personalized, new template). Readings ~140–190 words (v2).
| # | Title | Focus |
|---|-------|-------|
| 1 | Me and My World | to be (am/is/are) + personality adjectives *(adapt Dea S1)* |
| 2 | My Day | Present simple + -s rule, telling time *(adapt Dea S2)* |
| 3 | My School | have/has + there is/are, subjects & objects *(adapt Dea S3)* |
| 4 | My Home | Rooms, furniture, basic prepositions in/on/under |
| 5 | Clothes & Weather | "I'm wearing", "It's sunny", seasons |
| 6 | My Hobbies | like/love + -ing, days of the week |
| 7 | Always or Never? | Adverbs of frequency, my typical week |
| 8 | People & Jobs | Jobs vocab, describing other people (3rd person) |
| 9 | I Can Do It! | can/can't for ability, "Can you…?" |
| 10 | Review Quest 🗺️ | Cumulative quest game, certificate |

### Level 2 — Elementary (A2) `Level_2_Elementary/`
Sessions 1–3 are UPGRADED ADAPTATIONS of Dea S4–S6. Readings ~290–360 words (v2).
| # | Title | Focus |
|---|-------|-------|
| 1 | Food and Me | like/don't like, Do you like…?, food vocab *(adapt Dea S4)* |
| 2 | Animals & Nature | can/can't, animal features & habitats *(adapt Dea S5)* |
| 3 | My Town | there is/are + prepositions of place, directions *(adapt Dea S6)* |
| 4 | Right Now! | Present continuous vs present simple |
| 5 | Yesterday | Past simple regular + was/were |
| 6 | Story Time | Past simple irregular verbs, telling a short story |
| 7 | Bigger, Faster, Best | Comparatives & superlatives |
| 8 | Future Plans | going to, "would like to", my dream weekend |
| 9 | Rules & Advice | must / have to / should |
| 10 | Adventure Review 🏰 | Cumulative story-adventure game, certificate |

### Level 3 — Intermediate (B1) `Level_3_Intermediate/`
Likely entry level for strong 12-year-olds (e.g. Dea). Real opinions, longer talk turns. Readings ~350–440 words (v2).
| # | Title | Focus |
|---|-------|-------|
| 1 | My Story So Far | Present perfect vs past simple (ever/never/just/already) |
| 2 | What Was Happening | Past continuous, interrupted actions, storytelling |
| 3 | If I Had a Superpower | First & second conditional |
| 4 | Made in the World | Passive voice (present & past) |
| 5 | She Said WHAT?! | Reported speech basics |
| 6 | Phrasal Verb Detective | 12 high-frequency phrasal verbs |
| 7 | In My Opinion | Agreeing/disagreeing politely, mini-debate |
| 8 | Screens & Media | Media vocab, quantifiers, talking about habits |
| 9 | Travel the World | Travel English, used to, asking for info |
| 10 | Escape Room Review 🔐 | Cumulative escape-room game, certificate |

### Level 4 — Upper-Intermediate (B2) `Level_4_Upper_Intermediate/`
Abstract topics, teen-relevant. Readings ~480–520 words (v2).
| # | Title | Focus |
|---|-------|-------|
| 1 | Mysteries & Deduction | Modals of deduction (must/might/can't have) |
| 2 | The Time Machine | Mixed conditionals, wishes & regrets |
| 3 | Who, Which, Whose | Relative clauses (defining/non-defining) |
| 4 | The News Room | Passive reporting, headlines, spotting fake news |
| 5 | Say It Like You Mean It | Idioms & figurative language |
| 6 | The Art of Persuasion | Argumentation, linking words, counter-arguments |
| 7 | Future Worlds | Future perfect & continuous, predictions |
| 8 | Culture Shock | Gerund vs infinitive nuance, cultures & customs |
| 9 | Speak Like a Speaker | Presentation skills, discourse markers |
| 10 | The Grand Debate 🏛️ | Cumulative formal debate + review, certificate |

### Level 5 — Proficient (C1) `Level_5_Proficient/`
Nuance and naturalness. Readings ~600–760 words (v2), authentic-style.
| # | Title | Focus |
|---|-------|-------|
| 1 | Shades of Meaning | Connotation, register, word choice |
| 2 | Collocation Power | Natural word partnerships, avoiding "translated" English |
| 3 | Story Lab | Narrative tenses mastery, creative writing |
| 4 | Between the Lines | Inference, implied meaning, detecting bias |
| 5 | Humor & Wordplay | Puns, irony, sarcasm (age-appropriate) |
| 6 | Debate Club Pro | Hedging, concession, rebuttal |
| 7 | The Interview | Cleft sentences, emphasis, advanced Q&A |
| 8 | Academic Edge | Summary & essay skills, formal register |
| 9 | Englishes of the World | UK/US/global varieties, accents |
| 10 | Masterclass Review 🎓 | Capstone project, certificate |

### Level 6 — Near-Native (C2) `Level_6_Near_Native/`
Style, wit, cultural fluency. Authentic-style texts ~690–760 words (v2).
| # | Title | Focus |
|---|-------|-------|
| 1 | Style & Voice | Stylistics, shifting tone on demand |
| 2 | Real Talk | Informal registers, slang & internet English (age-appropriate) |
| 3 | The Persuader | Rhetoric, great speeches, rhetorical devices |
| 4 | Literature Corner | Analyzing excerpts (age-appropriate classics/YA) |
| 5 | Wit & Banter | Advanced humor, comebacks, politeness strategies |
| 6 | The Editor | Error-spotting, precision, improving real texts |
| 7 | Untranslatable | Idiomatic mastery, cultural references |
| 8 | Model UN | Formal negotiation & diplomacy language |
| 9 | Creator Studio | Scriptwriting / podcast project |
| 10 | Graduation 🎓 | Capstone showcase, near-native certificate |

---

## File naming
`Level_X_Name/session01.html` … `session10.html` (two digits). Hub = `index.html` in root. Assessment = `00_ASSESSMENT/placement.html` + `00_ASSESSMENT/scoring_guide.html`.

## Gold-standard exemplar
`Level_3_Intermediate/session01.html` is the reference implementation. Every generated session MUST reuse its CSS + JS engine verbatim (only content, colors accent, level badge, and quiz data change).
