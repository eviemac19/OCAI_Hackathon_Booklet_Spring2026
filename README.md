# Oxford Clinical AI Hackathon 2026 — Booklet

## Spring 2026 Edition

A self-contained set of Jupyter notebooks that walks you through building a clinical AI minimum viable application — from a customised ChatGPT to a fine-tuned small model — without needing prior coding experience and without leaving the OpenAI and HuggingFace open ecosystems.

---

## Welcome

This booklet is the post-event compendium of the Oxford Clinical AI Hackathon, held 6–8 April 2026 at the Cheng Kar Shun Digital Hub, Jesus College and the John Radcliffe Hospital, Oxford. Across three days, ten teams of clinicians, researchers, and data scientists built working clinical AI applications and presented them to a panel of judges. 

The event thesis was simple: Can you build an AI tool match FY1 competency? Each team dealth with different aspects of FY1 competency e.g. pass a final exam, read a CXR, write a discharge summary, etc. 
https://oerc.ox.ac.uk/ai-centre/ai-centre-events/oxford-clinical-ai-hackathon 
Academic sponsor: Oxford University AI Competency Centre
Technical Sponsor: OpenAI
Outputs: 
- Every team delivered a live demo, 80% of participants left with a working prototype
- Learning uplift was 3.59 to 7.17 confidence, Net Promoter Score of 76. 
- Learning archetypes transitioned from from AI learner to builder to governor.
  
## Who this booklet is for

- **Clinicians** who want to understand clinical AI well enough to evaluate it, build small tools for their own workflow, and contribute meaningfully to governance discussions.
- **Researchers and data scientists** who want to understand clinical reasoning well enough to build AI tools that clinicians will actually trust.
- **NHS and healthcare admin staff** whose frontline perspective makes them, in our experience, some of the most insightful contributors to clinical AI design.
- **Medical students and early-career clinicians** who want a hands-on grounding in clinical AI before it lands in their daily practice.

## What you'll be able to do by the end

- No-code: Customise ChatGPT and build Custom GPTs for clinical workflows, use Retrieval-Augmented Generation to ground AI outputs in trusted clinical references.
- Low-code: Train, validate, and explain a clinical machine learning model — including catching the kinds of data leakage that produce impressive metrics and dangerous tools.
- Code tasks: Fine-tune an small language model and integrate text-to-speech for a clinical voice loop.
- Governance: Recognise the difference between technical accuracy and clinical safety.  Write a model card, an acceptable-use statement, and a monitoring plan that would stand up to NHS AI / MHRA Software as a Medical Device scrutiny
  

## How the booklet is organised — full table of contents

### `00_setup/` — Environment and tools (one-time, ~30–60 minutes)

| File | What it is | Time |
| --- | --- | --- |
| `README.md` | Setup chapter — API key, three environment options (Colab, local, Codespaces), troubleshooting | 30–60 min |
| `00_hello_world_test.ipynb` | Five-step environment check that confirms everything is wired up | 5 min |
| `requirements.txt` | Pinned Python dependencies for the whole booklet | (reference) |
| `hello_world_test_outline.md` | Cell-by-cell plan for the test notebook (for re-builders) | (reference) |

### `01_foundations/` — Section 1: Foundations of AI (~5–6 hours)

The conceptual half of the booklet. No coding required to read it; small code cells are skippable.

| Notebook | What it covers | Time |
| --- | --- | --- |
| `01_introduction.ipynb` | Orientation,  3 rules to remember | 20 min |
| `02_what_is_ai.ipynb` | AI / ML / DL distinctions, neural networks, training, overfitting, evaluation | 40 min |
| `03_clinical_nlp.ipynb` | Language as a clinical signal — tokenisation, NER, summarisation, coding | 40 min |
| `03_clinical_nlp_demo_discharge_coding.ipynb` | Standalone — worked end-to-end discharge-coding pipeline (read-through) | 20 min |
| `04_clinical_imaging.ipynb` | How computers see images — CNNs, transfer learning, Grad-CAM | 35 min |
| `04_clinical_imaging_demo_radiology.ipynb` | Standalone — Stanford CXR deployment story, model card, MHRA pathway | 20 min |
| `05_llms_and_prompting.ipynb` | Pattern completion at scale, hallucination, prompt engineering, Custom GPTs, function calling | 45 min |
| `06_data_analytics.ipynb` | Features, splits, AUC, sensitivity, calibration, the data-leakage instinct | 40 min |
| `07_grounding_and_customisation.ipynb` | When prompting isn't enough — RAG, fine-tuning, the prompt → RAG → fine-tune decision tree | 40 min |
| `08_safety_governance_evaluation.ipynb` | Bias, accountability, model cards, EHIA, MHRA SaMD, governance as design | 40 min |

### `02_pipelines/` — Section 2: Foundations of AI Pipelines (~2–3 hours)

Concepts become code. Three modular pipeline notebooks using the heart-failure dataset throughout.

| Notebook | What it covers | Time |
| --- | --- | --- |
| `01_feature_pipeline.ipynb` | Source → inspect → drop the `time` leakage → handle imbalance → split → standardise | 45 min |
| `02_training_pipeline.ipynb` | Train four model families (LogReg, RF, GBoost, SVM); compare; threshold tuning; final test | 50 min |
| `03_inference_pipeline.ipynb` | SHAP + LIME triangulation, dynamic ipywidgets, GPT-grounded narrative, clinical guardrails | 60 min |

### `03_challenges/` — Section 3: Five clinical AI MVP challenges (~8–10 hours)

Each challenge is self-contained — clinical brief, dataset, 8–10 numbered Steps, demo-day rubric, model card, mentor's notes. Pick any order; *Challenge 3 is the densest if you only do one*.
## Recommended order

1. **`00_setup/` first.** Non-negotiable. All the notebooks depends on a working environment, and this is really worth dwelling over. 
2. **Section 1 — Foundations** 
3. **Section 2 — Pipelines.** This is where concepts become code. 
4. **Section 3 — Challenges**, in any order. They are independent.
5. **Glossary as a reference**
   
| Folder / notebook | Clinical question | Time |
| --- | --- | --- |
| `challenge_1_final_exam/challenge_1_final_exam.ipynb` | Can your AI pass an FY1 specimen exam? RAG over MedRAG + optional fine-tuning + LIME + guardrails | 90–120 min |
| `challenge_2_communication_ethics_empathy/challenge_2_communication_ethics_empathy.ipynb` | Can your AI scaffold a difficult clinical conversation safely? Five-framework dispatch + TTS bonus | 90–120 min |
| `challenge_3_data_analytics/challenge_3_data_analytics.ipynb` | Can your AI predict heart-failure mortality and explain why? *Includes the central data-leakage discovery* | 90–120 min |
| `challenge_4_imaging_pneumonia/challenge_4_imaging_pneumonia.ipynb` | Pneumonia yes/no on chest X-ray, and recognise when the input isn't a chest X-ray at all (OOD) | 90–150 min |
| `challenge_5_wearables/challenge_5_wearables.ipynb` | Wear → FHIR Observation → clinical snapshot for Mr David Chen's cardiologist | 120–180 min |

### Front-matter

| File | What it is |
| --- | --- |
| `README.md` | This page |
| `requirements.txt` | Top-level mirror of `00_setup/requirements.txt` |
| `Image assetss for OCAIH booklet 2026/` | Diagrams referenced from the foundations chapters |

### `appendix/` — Reference material

| File | What it is |
| --- | --- |
| `appendix/README.md` | Index to the appendix files |
| `appendix/glossary.ipynb` | Clinical-AI glossary — look up terms as they come up |
| `appendix/tech_stack.md` | Every Python library the booklet uses, with pinned versions, links to docs, and which chapter introduces each |
| `appendix/further_reading.md` | Consolidated citations from across the booklet — datasets, methodological papers, governance frameworks, clinical guidelines |
| `appendix/sponsors_and_credits.md` | Sponsors, venue, mentors, post-event survey contributors |
| `appendix/changelog.md` | Version history, starting at v1.0 |

## The five challenges

| Challenge | Clinical question |
| --- | --- |
| 1 — Final Exam | Can your AI pass a Foundation Year 1 specimen exam? |
| 2 — Communication, Ethics & Empathy | Can your AI summarise a complex case in SBAR and speak it aloud, safely? |
| 3 — Data Analytics | Can your AI predict heart failure mortality and explain why? |
| 4 — Imaging | Can your AI tell pneumonia from a normal chest X-ray, and tell you when the input isn't a chest X-ray at all? |
| 5 — Wearables | Can your AI ingest sensor data, convert it to FHIR, and write a clinical snapshot? |

## Time guidance

| Section | Time for self-study | Notes |
| --- | --- | --- |
| `00_setup/` | 30–60 minutes | One-time. Do this once and forget it. |
| Section 1 | 2–3 hours | Splits cleanly into 30–45 minute lectures. |
| Section 2 | 2–3 hours | Best done in one or two focused sittings. |
| Section 3 | 1.5–2 hours per challenge (≈ 8–10 hours total) | Each challenge stands alone. |
| **Total** | **≈ 12–17 hours** | A long weekend, or two evenings a week for two to three weeks. |

These are estimates from the live event, scaled for self-study. Add roughly 30% if you are completely new to Python.

## What you'll need

- A laptop with a stable internet connection.
- An OpenAI API key. Indicative budget: **$5–10** to complete all five challenges using GPT-4o-mini and TTS-1. Set up in `00_setup/`.
- A free HuggingFace account for the open datasets and models.
- Either Google Colab (free, recommended if you are new to Python), local JupyterLab, or GitHub Codespaces. Setup steps for all three are in `00_setup/`.

## Three rules to keep yourself and your patients safe

1. **Do not paste identifiable patient data into any hosted API.** This booklet uses public, de-identified, research-grade datasets exclusively. When you take what you've learned back into your own workflow, build with synthetic or de-identified data first.
2. **Treat any headline metric above 0.95 as a question, not an answer.** You'll meet this lesson properly in Section 2 and again in Challenge 3. The instinct to challenge a too-good-to-be-true result is the most valuable skill in this booklet.
3. **Governance is a design choice, not a compliance afterthought.** Every challenge ends with a governance section. Treat it as part of the build, not paperwork.

## Sponsors and acknowledgements

The Oxford Clinical AI Hackathon 2026 was made possible by the **Oxford University AI Competency Centre** and **OpenAI**, with hosting support from **Jesus College** and **Oxford University Hospitals NHS Foundation Trust**. The tooling used throughout this booklet is OpenAI's GPT-4o-mini, TTS-1, and Fine-tuning API, alongside open models and datasets from HuggingFace.

Thanks are due to the ten participating teams, the per-challenge mentors, the Python coaches, the OUH and Oxford clinicians who lent their clinical eye to the curriculum, and the twenty-nine post-event survey respondents whose feedback shaped this edition. The data leakage lesson in Challenge 3 is in this booklet because of you.

## Feedback and contact

This is the Spring 2026 Edition. We are already planning the next iteration. If you spot an error, find a notebook that won't run, or have a suggestion for a future edition, please write to us at:

**events@clinicalaipartners.org**

If the booklet helped you build something — small or otherwise — we'd love to hear about that too.

## Version

OCAI Hackathon Booklet · Spring 2026 Edition · v1.0

*Building the clinical AI workforce, one team at a time.*
