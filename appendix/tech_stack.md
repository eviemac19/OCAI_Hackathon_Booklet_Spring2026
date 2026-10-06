# Tech stack reference

Every library the booklet uses, why it's there, and where to look up the docs when you hit something unfamiliar. Versions are pinned in `requirements.txt` (booklet root and `00_setup/`) — copied here for at-a-glance reference.

The booklet's tooling rule (master brief §6) — **OpenAI sponsor models + free / open HuggingFace ecosystem only**. No other vendor models anywhere in the booklet.

---

## Core ML and data libraries

| Library | Pinned | What it does | Where it appears | Docs |
| --- | --- | --- | --- | --- |
| `openai` | `>=1.40.0,<2.0.0` | Sponsor OpenAI Python SDK — chat completions, fine-tuning, TTS | Section 0 (hello-world); Chapter 05 (LLMs and prompting); every Section 3 challenge | [platform.openai.com/docs](https://platform.openai.com/docs) |
| `huggingface_hub` | `>=0.23.0,<1.0.0` | Authentication and download client for HuggingFace datasets and models | Sections 0, 1, 2, 3 | [huggingface.co/docs/huggingface_hub](https://huggingface.co/docs/huggingface_hub) |
| `datasets` | `>=2.20.0,<4.0.0` | Loads `mstz/heart_failure`, `MedRAG/textbooks`, `alkzar90/NIH-Chest-X-ray-dataset` | All sections | [huggingface.co/docs/datasets](https://huggingface.co/docs/datasets) |
| `transformers` | `>=4.42.0,<5.0.0` | Tokenisers + models — used in Chapter 03 demo and Section 1 NLP examples | Chapter 03; Demo 1; Section 1 NLP demos | [huggingface.co/docs/transformers](https://huggingface.co/docs/transformers) |
| `scikit-learn` | `>=1.3.0,<2.0.0` | Logistic regression, random forest, gradient boosting, SVM; train/test/calibration utilities | Chapter 02, 06; Section 2; Challenges 3, 4 | [scikit-learn.org/stable/](https://scikit-learn.org/stable/) |
| `shap` | `>=0.45.0,<1.0.0` | Per-feature contributions for individual predictions | Chapter 06; Section 2; Challenge 3 | [shap.readthedocs.io](https://shap.readthedocs.io/) |
| `lime` | `>=0.2.0.1,<1.0.0` | Locally-interpretable model-agnostic explanations | Chapter 03 (LIME for NLP); Section 2; Challenges 1, 2, 3 | [github.com/marcotcr/lime](https://github.com/marcotcr/lime) |

## Data, viz, and notebook UI

| Library | Pinned | What it does | Where it appears |
| --- | --- | --- | --- |
| `pandas` | `>=2.0.0,<3.0.0` | DataFrame for tabular work | Everywhere tabular |
| `numpy` | `>=1.24.0,<2.2.0` | Numerical arrays. Upper bound is deliberate — SHAP and LIME work most reliably with NumPy < 2.2 | Everywhere |
| `matplotlib` | `>=3.7.0,<4.0.0` | All static plots in the booklet | Section 2; Demo 2; Challenges 3, 4 |
| `ipywidgets` | `>=8.0.0,<9.0.0` | Interactive sliders, buttons, output panels | Section 2 inference pipeline; Challenges 1, 2, 3 |

## Imaging stack (Challenge 4 only)

| Library | Pinned | What it does | Where it appears |
| --- | --- | --- | --- |
| `Pillow` | `>=10.0.0,<12.0.0` | Image I/O and pre-processing | Challenge 4 |
| `torch` | `>=2.0.0,<3.0.0` | PyTorch — used for ResNet-18 fine-tuning. Large download (~2 GB) | Challenge 4 |
| `torchvision` | `>=0.15.0,<1.0.0` | Pretrained ImageNet models, image transforms, data loaders | Challenge 4 |

> If you only intend to do Challenges 1–3, you can comment `torch` and `torchvision` out of `requirements.txt` and reinstall before starting Challenge 4.

## Specialist (per-challenge)

| Library | Pinned | Used in | Notes |
| --- | --- | --- | --- |
| `faiss-cpu` | latest | Challenge 1 | Vector index for RAG over MedRAG/textbooks. Install via `pip install faiss-cpu` if not already present |
| `sentence-transformers` | latest | Challenge 1 | Provides the `all-MiniLM-L6-v2` embedding model |
| `langchain-community`, `langchain-core` | latest | Challenge 1 | Document and vector-store abstractions for the RAG pipeline |
| `actipy` | latest | Challenge 5 | Axivity AX3 `.cwa` file parser. Verify the install command and current API at the time of running — the proposal v2 §11 flagged this as having shifted since the live event |
| `scipy` | bundled with sklearn | Chapter 04 | `scipy.ndimage.convolve` for the synthetic Sobel-edge demo |
| `joblib` | bundled with sklearn | Section 2 | Saves trained models and prepared data between notebooks |

## OpenAI-specific tooling

| Capability | Endpoint | Where it appears |
| --- | --- | --- |
| Chat completions | `client.chat.completions.create(...)` | Everywhere LLMs are used |
| Structured output (JSON schema) | `response_format={"type": "json_object"}` | Chapter 05; Section 2 inference; Challenge 3 narrative |
| Function calling (tool use) | `tools=[...]` | Chapter 05 |
| Fine-tuning | `client.fine_tuning.jobs.create(...)` | Challenge 1 (gated behind `RUN_FINE_TUNING` flag) |
| Text-to-speech (TTS-1 / `gpt-4o-mini-tts`) | `client.audio.speech.with_streaming_response.create(...)` | Challenge 2 (bonus) |

The default model throughout is **`gpt-4o-mini`**. It is the cheapest in the GPT-4 family at time of writing and is sufficient for every task in the booklet.

## Indicative cost — completing all five challenges

| Item | Approximate cost |
| --- | --- |
| All chapters and challenges using GPT-4o-mini | $1–3 |
| Challenge 2 TTS bonus (a few minutes of speech) | < $0.50 |
| Challenge 1 fine-tuning (if you flip the gate) | $3–5 |
| **Total budget recommendation** | **$10–15** as the OpenAI hard limit |

Section 0 walks through setting the limit at platform.openai.com/account/limits before generating any keys.

---

*Appendix · Tech stack reference · OCAI Booklet · Spring 2026 Edition*
