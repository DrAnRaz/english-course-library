# SESSION_NOTES — English Course Library

## 2026-07-07 — Teljes library build (folyamatban)

**Mit csináltunk:**
- Dea-kurzus (6 session) pedagógiai audit: erős rituálé-struktúra, DE A2-plafon, listening-hiány (S2–S6), alábecsült időzítés, falba-írt olvasmányok, hard-coded "Dea"
- Spec lock (Aniko döntései): kids&teens 9–15 · minden egyben · új GitHub Pages site
- Új struktúra: `English_Course_Library/` — 7 szint (0=pre-A1 … 6=C2) × 10 session + placement assessment
- `CURRICULUM.md` (locked spec, 70 session térkép), gold exemplar: `Level_3_Intermediate/session01.html` (böngészőben verifikálva: quiz engine, TTS, teacher mode PIN `teach`, agenda, autosave OK)
- `00_ASSESSMENT/placement.html` (44 tagged item, ladder + speaking rubric + auto ajánlás — B1-szimuláció helyesen L3-at adott) + `scoring_guide.html`
- `index.html` hub + `TEACHER_GUIDE.html`
- 21 párhuzamos agent generálta a sessionöket a spec szerint (GENERATION_SPEC.md scratchpadben)
- Wave 1 KÉSZ + független verifikáció: L1, L2, L3 mind a 30 session PASS (markerek, méret, no-Dea case-sensitive check)
- Git repo a mappában (Dea-minta), push → **https://github.com/DrAnRaz/english-course-library** (public), GitHub Pages ENABLED → **https://dranraz.github.io/english-course-library/**

**Folyamatban:** Wave 2 (12 agent): L0, L4, L5, L6 — 40 session. Utána: verifikáció + végső commit/push + élő URL smoke test.

**Érintett fájlok:** minden e mappában; Dea_EnglishCourse érintetlen maradt.

**Nyitott kérdések:**
- Dea következő órájára: futtasd le vele a placement-et (várható: L3)
- Teacher PIN egyszerű (`teach`) — tudatos döntés, nem biztonsági határ
