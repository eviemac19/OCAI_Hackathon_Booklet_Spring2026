# Oxford Clinical AI Hackathon 2026 — Booklet

## Spring 2026 Edition · public selection

Jupyter notebooks from the Oxford Clinical AI Hackathon that walk you through building and explaining a clinical AI model, from raw data to a governed, demo-ready tool. No prior coding experience is needed.

---

## Welcome

This booklet is the after-event compendium of the Oxford Clinical AI Hackathon, held 6–8 April 2026 at the Cheng Kar Shun Digital Hub, Jesus College and the John Radcliffe Hospital, Oxford. Across three days, ten teams of clinicians, researchers, and data scientists built working clinical AI applications and presented them to a panel of judges. Every team delivered a live demo. The post-event survey returned an overall rating of 4.49 out of 5 and a Net Promoter Score of +63.

The notebooks here are the lectures, notebooks, and mentor notes from that event, re-edited so you can work through them at your own pace.

If you were at the event: this is the same material, with the lessons we learned along the way folded in and the rough edges smoothed. If you weren't: welcome — you are in good company. Most of our live-event participants started with no coding experience. The booklet is built for that.

## Impact — Spring 2026

![Oxford Clinical AI Hackathon Spring 2026 — impact in one page](assets/impact_one_page_spring2026.png)

- **66** clinicians, researchers and scientists from four continents, in ten teams
- **80%** of survey respondents reported a fully functional prototype by Demo Day
- Self-rated ability to build a clinical AI pipeline rose from **3.59 to 7.17** out of 10
- Overall rating **4.49 / 5**; Net Promoter Score **+63**

*Source: post-event survey, completed by 41 of the 66 attendees.*

The event sat at the interface between a frontier AI lab and clinicians who were new to building with AI. The lab brought the tools; the cohort brought the clinical problems; our curriculum did the translating.

Event page at the Oxford University AI Competency Centre: [oerc.ox.ac.uk/ai-centre/ai-centre-events/oxford-clinical-ai-hackathon](https://oerc.ox.ac.uk/ai-centre/ai-centre-events/oxford-clinical-ai-hackathon)

## What is in this repository

This repository is a public selection from the full booklet. It contains the setup chapter, the complete pipelines section, one of the five challenges, and the reference appendix.

### `00_setup/` — Environment and tools (one-time, ~30–60 minutes)

| File | What it is | Time |
| --- | --- | --- |
| `README.md` | Setup chapter — API key, three environment options (Colab, local, Codespaces), troubleshooting | 30–60 min |
| `00_hello_world_test.ipynb` | Five-step environment check that confirms everything is wired up | 5 min |
| `requirements.txt` | Pinned Python dependencies | (reference) |
| `hello_world_test_outline.md` | Cell-by-cell plan for the test notebook (for re-builders) | (reference) |

### `02_pipelines/` — Section 2: Foundations of AI Pipelines (~2–3 hours)

Concepts become code. Three modular pipeline notebooks using the heart-failure dataset throughout.

| Notebook | What it covers | Time |
| --- | --- | --- |
| `01_feature_pipeline.ipynb` | Source → inspect → drop the `time` leakage → handle imbalance → split → standardise | 45 min |
| `02_training_pipeline.ipynb` | Train four model families (LogReg, RF, GBoost, SVM); compare; threshold tuning; final test | 50 min |
| `03_inference_pipeline.ipynb` | SHAP + LIME triangulation, dynamic ipywidgets, GPT-grounded narrative, clinical guardrails | 60 min |

### `03_challenges/` — Section 3: Challenge 4, Imaging

A self-contained challenge — clinical brief, dataset, numbered Steps, demo-day rubric, model card, mentor's notes.

| Folder / notebook | Clinical question | Time |
| --- | --- | --- |
| `challenge_4_imaging_pneumonia/challenge_4_imaging_pneumonia.ipynb` | Pneumonia yes/no on chest X-ray, and recognise when the input isn't a chest X-ray at all (out-of-distribution detection) | 90–150 min |

### `appendix/` — Reference material

| File | What it is |
| --- | --- |
| `appendix/README.md` | Index to the appendix files |
| `appendix/glossary.ipynb` | Clinical-AI glossary — look up terms as they come up |
| `appendix/tech_stack.md` | The Python libraries the booklet uses, with pinned versions and links to docs |
| `appendix/further_reading.md` | Consolidated citations — datasets, methodological papers, governance frameworks, clinical guidelines |
| `appendix/sponsors_and_credits.md` | Sponsors, venue, mentors, post-event survey contributors |
| `appendix/changelog.md` | Version history |

`LICENSE.md` and `CITATION.cff` at the top level set out the reuse terms and how to cite the booklet.

### The full booklet

The full booklet also has a conceptual section (Section 1 — Foundations of AI) and four more challenges: Final Exam, Communication Ethics & Empathy, Data Analytics, and Wearables. They are used in our live programmes and are not part of this public selection.

You will see cross-references to them in the notebooks here, for example *Chapter 06* or *Challenge 3*. The notebooks in this repository do not load any files from them. If you would like to know more about the full curriculum, write to us at the address below.

## Who this booklet is for

- **Clinicians** who want to understand clinical AI well enough to evaluate it, build small tools for their own workflow, and contribute meaningfully to governance discussions.
- **Researchers and data scientists** who want to understand clinical reasoning well enough to build AI tools that clinicians will actually trust.
- **NHS and healthcare admin staff** whose frontline perspective makes them, in our experience, some of the most insightful contributors to clinical AI design.
- **Medical students and early-career clinicians** who want a hands-on grounding in clinical AI before it lands in their daily practice.

The most useful learning happens when these groups work together. If you can find a study partner from a different background, do.

## What you'll be able to do by the end

- Prepare a clinical dataset for modelling — including catching the kind of data leakage that produces impressive metrics and dangerous tools.
- Train, validate, and compare several model families, and choose a decision threshold as a clinical decision rather than a default.
- Explain an individual prediction with SHAP and LIME, and generate a clinical narrative that is grounded in the model output and held by guardrails.
- Fine-tune an image classifier on chest X-rays, and detect when an input is not a chest X-ray at all.
- Write a model card, an acceptable-use statement, and a monitoring plan.
- Recognise the difference between technical accuracy and clinical safety, and tell which one a vendor is actually showing you.

## Recommended order

1. **`00_setup/` first.** Non-negotiable. Everything later depends on a working environment.
2. **`02_pipelines/` next, in order.** Each notebook saves what the next one loads. Take your time on the feature pipeline notebook in particular — the data leakage example is the single most important lesson in the booklet.
3. **Challenge 4** once the pipelines make sense. It re-points the same pipeline at an imaging problem.
4. **Glossary as a reference**, not a chapter. Open it when you hit a term you don't know.

## Time guidance

| Section | Time for self-study | Notes |
| --- | --- | --- |
| `00_setup/` | 30–60 minutes | One-time. Do this once and forget it. |
| Section 2 — Pipelines | 2–3 hours | Best done in one or two focused sittings. |
| Challenge 4 — Imaging | 1.5–2.5 hours | Depends on download speed and whether you have a GPU. |
| **Total** | **≈ 4–6 hours** | |

These are estimates from the live event, scaled for self-study. Add roughly 30% if you are completely new to Python.

## What you'll need

- A laptop with a stable internet connection.
- An OpenAI API key for the environment check and the narrative steps. The notebooks here use GPT-4o-mini and cost very little to run; `00_setup/` walks you through setting a hard spending limit before you generate a key.
- A free HuggingFace account for the open datasets and models.
- Either Google Colab (free, recommended if you are new to Python), local JupyterLab, or GitHub Codespaces. Setup steps for all three are in `00_setup/`.

## Three rules to keep yourself and your patients safe

1. **Do not paste identifiable patient data into any hosted API.** This booklet uses public, de-identified, research-grade datasets exclusively. When you take what you've learned back into your own workflow, build with synthetic or de-identified data first.
2. **Treat any headline metric above 0.95 as a question, not an answer.** You'll meet this lesson properly in Section 2. The instinct to challenge a too-good-to-be-true result is the most valuable skill in this booklet.
3. **Governance is a design choice, not a compliance afterthought.** The challenge ends with a governance section. Treat it as part of the build, not paperwork.

## Sponsors and acknowledgements

The Oxford Clinical AI Hackathon 2026 was made possible by the **Oxford University AI Competency Centre** and **OpenAI**, with hosting support from **Jesus College** and **Oxford University Hospitals NHS Foundation Trust**.

This edition uses OpenAI's GPT-4o-mini for the narrative steps, alongside open models and datasets from HuggingFace. The clinical framing and the pipeline design do not depend on one vendor; the model calls sit in a small number of cells and can be swapped.

Thanks are due to the ten participating teams, the per-challenge mentors, the Python coaches, the OUH and Oxford clinicians who lent their clinical eye to the curriculum, and the post-event survey respondents whose feedback shaped this edition. The data leakage lesson is in this booklet because of you.

## Licence and citation

© 2026 Clinical AI Partners Ltd. This repository carries two sets of terms; the full wording is in [`LICENSE.md`](LICENSE.md).

- **Code is open.** The code cells in the notebooks, and the requirements files, are released under the MIT Licence. Use, adapt and build on them freely.
- **Teaching text is copyright, all rights reserved.** Treat it as you would an academic paper: read it, learn from it, and quote short passages with a citation. Please ask before republishing, adapting, or teaching from it.
- **Datasets and models** belong to their own providers and keep their own licences.

To cite this booklet:

> Clinical AI Partners Oxford (2026). *Oxford Clinical AI Hackathon Booklet, Spring 2026 Edition* (v1.0.1). https://github.com/eviemac19/OCAI_Hackathon_Booklet_Spring2026

For permission to reuse the teaching text, write to **events@clinicalaipartners.org**.

## Feedback and contact

If you spot an error, find a notebook that won't run, or have a suggestion for a future edition, please write to us at:

**events@clinicalaipartners.org**

If the booklet helped you build something — small or otherwise — we'd love to hear about that too.

## Version

OCAI Hackathon Booklet · Spring 2026 Edition · v1.0.1

*Building the clinical AI workforce, one team at a time.*
