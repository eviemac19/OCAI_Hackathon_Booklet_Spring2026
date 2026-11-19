# Changelog

Version history for the OCAI Hackathon Booklet — Spring 2026 Edition. Reverse chronological.

---

## v1.0.1 — 19 November 2026 — public selection tidied

- README now describes the notebooks actually published in this repository, with a note on the full booklet.
- Cross-references to internal planning documents removed from the notebooks and appendix.
- Challenge 4 section references now point to the notebook's own numbered Steps.
- AI-ENGAGE citation in `further_reading.md` corrected (authors, title, journal).
- Expected spend and recommended API hard limit stated separately in `tech_stack.md`.
- Event figures aligned with the final post-event survey (41 of 66 attendees).
- Licence terms and a citation file added: code under the MIT Licence, teaching text copyright with all rights reserved.

---

## v1.0 — 26 April 2026 — initial release

The first self-study compendium edition. Re-authored from the live-event source materials of the Oxford Clinical AI Hackathon (6–8 April 2026), incorporating the post-event survey feedback and the lessons learned at the event.

### Structure

- Four sections (`00_setup`, `01_foundations`, `02_pipelines`, `03_challenges`) plus reference materials. This repository publishes a selection; see the top-level README.
- Per-challenge template applied uniformly: clinical brief, dataset, setup, numbered Steps, demo-day rubric, model card, mentor's notes.

### Improvements over the live-event materials

The booklet is *not* a port — it is a re-authoring that builds the lessons learned at the event into the notebooks. Material changes in the notebooks published here:

| What | Fixed |
| --- | --- |
| Heart-failure dataset's `time` column — used as a feature in the original 2020 paper and live-event notebook, producing AUC > 0.95 by leakage | Removed; the discovery-and-removal of the leak is now Section 2's central teaching moment |
| Challenge 4 multi-task scope creep — the NIH dataset was originally used for COVID, lung opacity, multi-class disease detection, and pneumonia simultaneously | Narrowed to *pneumonia binary only*; the quality checks at the end of the notebook confirm the narrowing held |
| Hard-coded feature names in widget code (silent failure when datasets evolved) | All widgets now build dynamically from SHAP top features |
| `SYSTEM_PROMPT` redefinition in later cells | Single canonical prompt per notebook, defined once at the top, used everywhere |
| HuggingFace dataset loads with no fallback | Every load paired with a try/except and a fallback source |
| Dataset column-name drift between releases (`DEATH_EVENT` vs `is_dead`) | Pinned with a single conditional line at the top of every notebook that loads heart-failure data |
| Pre-installation lag for SHAP / LIME on Colab (60-second mid-notebook delay) | All dependencies pinned in `requirements.txt` and installed in the setup chapter, never mid-notebook |

### Authoring notes

- The named patients and clinicians who appear in the booklet's worked examples are fictional. They are simulated; their cases are illustrative.
- The booklet uses the Chicco & Jurman (2020) heart-failure dataset, the NIH ChestX-ray dataset (Wang *et al.* 2017), the MedRAG/textbooks corpus (Xiong *et al.* 2024), and the Capture-24 wearables dataset (Doherty *et al.* 2017) — all open and public; full citations in `further_reading.md`.

---

## Backlog for future editions

Not in v1.0.

- External validation passes on each predictive challenge (Challenge 3 against MIMIC subsets; Challenge 4 against CheXpert / OpenI). Honest reporting of the internal-vs-external gap.
- Calibration analysis — predicted-vs-observed reliability diagram and temperature scaling.
- Subgroup performance audits for every predictive challenge — sex, age band, comorbidity. Aggregate metrics hide what these surface.
- Whisper-transcribed dictation layer for Challenge 4 — radiologist audio note as second source of clinical context.

If you would like to contribute to a future edition — by writing back about an error, a confusing passage, or a successful adaptation in your own setting — write to **events@clinicalaipartners.org**.

---

*Appendix · Changelog · OCAI Booklet · Spring 2026 Edition*
