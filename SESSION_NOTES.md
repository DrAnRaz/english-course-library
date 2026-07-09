# SESSION_NOTES — English Course Library

## 2026-07-07 — Teljes library build (KÉSZ ✅)

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

**Befejezve:** Wave 2 is kész (1 agent API-hiba után resume-olva, L6 s03 pótolva). Mind a 70 session PASS a 12-markeres verifikáción; L0 s01 + L6 s10 böngészőben is tesztelve (quiz engine, certificate név-sync). 2 commit pusholva, Pages build BUILT, élő URL-ek 200 OK (index, placement, L0/L3/L4/L5/L6 minták, teacher guide).

**Érintett fájlok:** minden e mappában; Dea_EnglishCourse érintetlen maradt.

**2026-07-07 este — 2 javítás (Aniko visszajelzésére):**
- TTS `say()` robusztussá téve mind a 71 fájlban: cancel→speak race fix (80ms defer), `resume()` a beragadt paused állapotra, explicit angol hang választás, 10s keep-alive hosszú felolvasáshoz (Chrome ~15s-nél vágta volna). Playwright-tal verifikálva.
- Anti-cheat: minden quiz válaszopció Fisher–Yates shuffle-t kap MINDEN betöltésnél (buildQuiz + buildTagged engine) — a helyes válasz pozíciója diákonként/frissítésenként más. Verifikálva: 8/10 quiz sorrend változott két betöltés között, pontozás intakt.

**Nyitott kérdések:**
- Dea következő órájára: futtasd le vele a placement-et (várható: L3)
- Teacher PIN egyszerű (`teach`) — tudatos döntés, nem biztonsági határ

## 2026-07-09 — v2 nagyjavítás: tanár/diák nézet szétválasztás + pedagógiai audit (KÉSZ ✅ + LIVE)

**Kiváltó ok (Aniko, Dea holnap 9:00 óra):** képernyőmegosztáskor a diák látta a tanárnak szánt infót (percek, session-cím, "Say:" script), + panasz: a Step-1 goal ígér grammatikát, de a tanítóblokk nem látszik.

**Mit csináltunk:**
- **Teljes 70-session pedagógiai audit** (7 párhuzamos Explore agent, 8-pontos rubrika A–H). Nincs CRITICAL sehol; A (goal↔teaching) és C (reading↔quiz) tiszta minden szinten. Systemic gapek: (F) házi-lánc megszakad, (H) Step 3/Step 8 hiányzó teacher-note, (H) gendered "she/her" a diákra. Audit-jelentések: scratchpad/audit_L0..L6.md.
- **9 javítás (FIX_SPEC.md, locked):** 1) teacher-view CSS gate — `.timing`+`.zoom-cue` csak teacher-mode-ban; 2) badge-ből "≈NN min core" törölve; 3) Step-1 goal split (rövid diák-sor + teljes script a teacher-note-ba "Say:"-ként — nem lövi le a Step-5 grammar reveal-t); 4) **olvasmányok +40% MINDEN sessionben** (minden meglévő mondat verbatim, quiz-kulcsok nem sérülnek); 5) "🔎 Watch for…" noticing cue a reading-step tetején (nem-review); 6) házi-check lánc helyreállítva (Step-1 note "Homework check (S{N-1})"); 7) mind a 8 stepnek van teacher-note; 8) gender-semleges tanári cue (they/their); 9) tartalmi lyukak (L2 habitat frame, L4 s04 fake-news frame + s07 bonus, L5 s04 bias / s08 summary frame + s03 quiz-item fix, **L6 s04 imagery/symbolism/foreshadowing rulebox = a könyvtár legélesebb hiánya**, L6 s03 anaphora-claim javítás).
- Végrehajtás: CSS gate script (mind a 70 fájl), majd 7 párhuzamos writer agent (1/szint). L5+L6 Fable-limitbe futott → Opusra váltás után 1 completion agent fejezte be (L5 s10 + L6 s07–s10).
- **Verifikáció:** verify_tight.py 70/70 PASS (css-gate ×1, nincs badge-min, 8 teacher-note/fájl, nincs diák-"she/her" leak, reading ≥1.25×, nincs látható goal-script). Playwright smoke-test L2 s01-en: diák-nézet mindent rejt + új goal-sor + noticing cue; teacher-mode mindent felfed ("Say: …"). Live rebuild GitHub Pages "built" @0bc49e8, no-cache fetch megerősítve.
- TEACHER_GUIDE.html §2 átírva: **"student drives"** default Zoom-flow (a diák nyitja a linket saját gépén és ő oszt képernyőt; tanár privát teacher-mode ablakban) + dual-window fallback. CURRICULUM.md → v2 (reading szó-count spec, teacher-view gating spec).

**Érintett fájlok:** mind a 70 session + CURRICULUM.md + TEACHER_GUIDE.html + SESSION_NOTES.md. Commit `0bc49e8` pusholva, LIVE.

**Holnapi órához (Dea):** L2 s01 "Food and Me" — https://dranraz.github.io/english-course-library/Level_2_Elementary/session01.html (előző javaslat változatlan). Új munkafolyamat: Dea nyitja a linket, ő oszt képernyőt; te teacher-mode-ban (PIN `teach`) privát ablakban vezeted.

**Nyitott:** semmi kritikus. (Opcionális későbbre: TTS a megnyújtott olvasmányoknál ~15s-nél tovább tarthat — a meglévő 10s keep-alive engine kezeli, de hosszú C1/C2 szövegnél érdemes élőben ellenőrizni.)
