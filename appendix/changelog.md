# Changelog

Version history for the OCAI Hackathon Booklet — Spring 2026 Edition. Reverse chronological.

---

## v1.0 — 26 April 2026 — initial release

The first self-study compendium edition. Re-authored from the live-event source materials of the Oxford Clinical AI Hackathon (6–8 April 2026), incorporating the post-event survey feedback (n=29) and the v2.0 lessons-learned items.

### Structure

- 22 Jupyter notebooks across four sections (`00_setup`, `01_foundations`, `02_pipelines`, `03_challenges`) plus front-matter and reference materials.
- Per-challenge template applied uniformly: clinical brief, dataset, setup, numbered Steps, demo-day rubric, model card, mentor's notes.
- Total reading + run time: approximately 12–17 hours (Section 1: 5–6 hr; Section 2: 2–3 hr; Section 3: 8–10 hr; setup: 30–60 min one-time).

### Improvements over the live-event materials

The booklet is *not* a port — it is a re-authoring that fixes the v2.0 lessons-learned items inline. Material changes:

| What | Fixed |
| --- | --- |
| Heart-failure dataset's `time` column — used as a feature in the original 2020 paper and live-event notebook, producing AUC > 0.95 by leakage | Removed; the discovery-and-removal of the leak is now Section 2 + Challenge 3's central teaching moment |
| Challenge 4 multi-task scope creep — the NIH dataset was originally used for COVID, lung opacity, multi-class disease detection, and pneumonia simultaneously | Narrowed to *pneumonia binary only* per scope brief v2; §9 grep checks confirm the narrowing held |
| Challenge 5 broken starter code, dataset, and reference paper (lowest-rated track in the post-event survey) | From-scratch rebuild per proposal v2: parallel rule-based (Hildebrand cut-points) + supervised classifiers, FHIR Observation output, Mr David Chen worked example |
| Challenge 1 fine-tuning was a stub at the live event (org permissions blocked it) | Real fine-tuning code restored, gated behind a `RUN_FINE_TUNING` flag — readers with paid OpenAI accounts can run it |
| Challenge 1 had a broken benchmark cell (Cell 24 in source) flagged by the cheat sheet as *ignore this* | Removed; the working benchmark logic was folded into Step 6's full 20-question test set |
| Challenge 1 product definition appeared in two contradictory forms (FY1 colleague vs. medical-school finals bot) | Tightened to a single statement at the top of the notebook |
| Hard-coded feature names in widget code (silent failure when datasets evolved) | All widgets now build dynamically from SHAP top features (master brief §7 v2.0 lesson) |
| `SYSTEM_PROMPT` redefinition in later cells (the "Cell 36 wins" bug) | Single canonical prompt per notebook, defined once at the top, used everywhere |
| HuggingFace dataset loads with no fallback | Every load paired with a try/except + UCI / inline-corpus fallback (master brief §9) |
| Dataset column-name drift between releases (`DEATH_EVENT` vs `is_dead`) | Pinned with a single conditional line at the top of every notebook that loads heart-failure data |
| Pre-installation lag for SHAP / LIME on Colab (60-second mid-notebook delay) | All dependencies pinned in `requirements.txt` and installed in the setup chapter, never mid-notebook |
| Vendor-exclusivity inconsistency in Day 1 lectures (Anthropic, Claude, Gemini, LLaMA, etc. mentioned 28+ times across L4–L6) | Re-edited; zero hits for non-OpenAI vendor names across the booklet (one named LLaMA mention in Chapter 07 as the canonical open-weight family example, per option (c) sign-off) |

### Authoring contributions

- Dr Priya Mehta (Chapter 02), Mrs Amara Osei (Chapter 03), Dr Anika Sharma (Chapter 04), Mr Raymond Holloway (Chapter 05), and Mr David Chen (Demo 1, Challenge 5) appear as the booklet's recurring fictional clinical anchors. They are simulated; their cases are illustrative.
- The booklet uses the Chicco & Jurman (2020) heart-failure dataset, the NIH ChestX-ray dataset (Wang *et al.* 2017), the MedRAG/textbooks corpus (Xiong *et al.* 2024), and the Capture-24 wearables dataset (Doherty *et al.* 2017) — all open and public; full citations in `further_reading.md`.

### Known open items at v1.0 release

- **Capture-24 dataset URL and licence text** — readers download the data themselves (Wearables proposal v2 §3 deliberately frames this as the first lesson of Challenge 5). Verify the live URL at the time of running.
- **`actipy` API surface** — proposal v2 §11 noted this may have shifted since the live event. The Challenge 5 notebook uses `actipy.read_device(...)` with the v2-period signature; readers should verify against the current documentation.
- **Challenge 5 LOINC codes** — the codes in the FHIR Observation step are flagged `# placeholder — verify` for clinical-SME confirmation against the latest LOINC release before any production deployment.
- **Image-asset folder spelling** — the booklet's image folder is named `Image assetss for OCAIH booklet 2026/` (a typo from the original; preserved as-is to match the file system). Chapter 02's image link references this exact name. Renaming the folder requires updating the link.

---

## v2.x and beyond — backlog (post-release)

For future editions. Not in v1.0.

- External validation passes on each predictive challenge (Challenge 3 against MIMIC subsets; Challenge 4 against CheXpert / OpenI). Honest reporting of the internal-vs-external gap.
- UK Core FHIR profile mapping for Challenge 5 (proposal §10.E extension path).
- Calibration analysis added to Challenge 3 — predicted-vs-observed reliability diagram and temperature scaling.
- Subgroup performance audits for every predictive challenge — sex, age band, comorbidity. Aggregate metrics hide what these surface.
- Whisper-transcribed dictation layer for Challenge 4 — radiologist audio note as second source of clinical context.
- A second wear longitudinal trend for Challenge 5 — activity adherence over weeks rather than a single snapshot.

If you would like to contribute to a future edition — by writing back about an error, a confusing passage, or a successful adaptation in your own setting — write to **events@clinicalaipartners.org**.

---

*Appendix · Changelog · OCAI Booklet · Spring 2026 Edition*
