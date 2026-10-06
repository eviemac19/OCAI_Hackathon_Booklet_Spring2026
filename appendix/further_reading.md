# Further reading

Citations consolidated from across the booklet — datasets, methodological papers, governance frameworks, clinical guidelines, and the small handful of *go beyond* references the chapters point at. Grouped by where they first appear.

This list is **not** comprehensive academic coverage. It is the references the booklet actually relies on, plus a small set of *next steps* a reader who wants to dig deeper would benefit from. The clinical-AI literature is large and moves fast; this is the ladder, not the library.

---

## Section 0 — Setup

- OpenAI platform documentation — [platform.openai.com/docs](https://platform.openai.com/docs/)
- HuggingFace Hub authentication — [huggingface.co/docs/hub/security-tokens](https://huggingface.co/docs/hub/security-tokens)
- Google Colab user guide — [research.google.com/colaboratory/faq.html](https://research.google.com/colaboratory/faq.html)

---

## Section 1 — Foundations of AI

### Chapter 02 — What is AI

- ICO definition of AI — [ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/artificial-intelligence/](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/artificial-intelligence/)
- Allas, T. & Goodman, S. *AI in business: from talk to action.* McKinsey UK, July 2025.
- Hennessy, R. & Murphy, P. *AI-ENGAGE: a multicentre study of structured AI engagement in higher education.* 2025.

### Chapter 03 — Clinical NLP

- Vaswani, A. *et al.* *Attention is All You Need.* NeurIPS 2017 — the transformer paper.
- BioMedRoBERTa — [huggingface.co/allenai/biomed_roberta_base](https://huggingface.co/allenai/biomed_roberta_base)
- Lee, J. *et al.* *BioBERT: a pre-trained biomedical language representation model for biomedical text mining.* Bioinformatics, 2020.
- ICO and NHS England de-identification guidance under UK GDPR.

### Chapter 04 — Clinical Imaging

- Wang, X. *et al.* *ChestX-ray8: Hospital-scale Chest X-ray Database and Benchmarks on Weakly-Supervised Classification and Localization of Common Thorax Diseases.* IEEE CVPR 2017.
- He, K. *et al.* *Deep Residual Learning for Image Recognition.* IEEE CVPR 2016 — the ResNet paper.
- Selvaraju, R. R. *et al.* *Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization.* IEEE ICCV 2017.
- Rajpurkar, P. *et al.* *CheXNet: Radiologist-Level Pneumonia Detection on Chest X-Rays with Deep Learning.* arXiv:1711.05225 (2017) — the Stanford pneumonia paper at the centre of Demo 2.

### Chapter 05 — LLMs and prompting

- OpenAI prompt-engineering guide — [platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering)
- Brown, T. *et al.* *Language Models are Few-Shot Learners.* NeurIPS 2020 — the GPT-3 paper.
- Ouyang, L. *et al.* *Training language models to follow instructions with human feedback.* NeurIPS 2022 — the InstructGPT / RLHF paper.
- Lewis, P. *et al.* *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.* NeurIPS 2020.

### Chapter 06 — Data analytics

- Chicco, D. & Jurman, G. *Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone.* BMC Medical Informatics and Decision Making, 2020. *Note: the paper used the `time` column as a feature; the data-leakage lesson in this booklet is the correction.*
- Saito, T. & Rehmsmeier, M. *The precision-recall plot is more informative than the ROC plot when evaluating binary classifiers on imbalanced datasets.* PLoS ONE, 2015.
- DeLong, E. R. *et al.* *Comparing the areas under two or more correlated receiver operating characteristic curves.* Biometrics, 1988 — the canonical reference for AUC comparison.

### Chapter 07 — Grounding and customisation

- OpenAI fine-tuning documentation — [platform.openai.com/docs/guides/fine-tuning](https://platform.openai.com/docs/guides/fine-tuning)
- Xiong, G. *et al.* *MedRAG: Benchmarking Retrieval-Augmented Generation for Medicine.* arXiv:2402.13178 (2024).
- HuggingFace embedding model — [huggingface.co/sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)

### Chapter 08 — Safety, governance, evaluation

- General Medical Council. *Good Medical Practice* (2024 update).
- MHRA. *Software and AI as a Medical Device — change programme.* Ongoing — see [gov.uk/government/publications/software-and-ai-as-a-medical-device-change-programme](https://www.gov.uk/government/publications/software-and-ai-as-a-medical-device-change-programme).
- NHS England. *AI Ethics Initiative — Algorithmic Impact Assessment (AIA).*
- NHS England. *Equality and Health Inequalities Assessment (EHIA) framework.*
- DCB0129 / DCB0160 — *Clinical Risk Management for Health IT Systems.* NHS Digital.
- EU AI Act (2024) — the high-risk classification of clinical AI.

---

## Section 2 — Pipelines

The pipeline section uses the heart-failure dataset and citations are consolidated above (Chapter 06). Additional methodology references:

- Saito & Rehmsmeier (2015) — see Chapter 06.
- Vickers, A. J. & Elkin, E. B. *Decision curve analysis: a novel method for evaluating prediction models.* Medical Decision Making, 2006 — for readers who want to extend Section 2's threshold tuning into formal clinical-utility analysis.

---

## Section 3 — Challenges

### Challenge 1 — Final Exam (RAG + fine-tuning)

- Xiong (2024) — see Chapter 07.
- OpenAI fine-tuning best practices — [platform.openai.com/docs/guides/fine-tuning](https://platform.openai.com/docs/guides/fine-tuning).

### Challenge 2 — Communication, Ethics, Empathy

- Baile, W. F. *et al.* *SPIKES — A Six-Step Protocol for Delivering Bad News.* The Oncologist, 2000.
- Gillick *v* West Norfolk and Wisbech AHA [1985] UKHL 7 — the case establishing Gillick competence and the Fraser Guidelines.
- General Medical Council. *Good Medical Practice* (2024). Confidentiality, paragraphs 64–65 (safeguarding precedence).
- Resuscitation Council UK. *ReSPECT process and DNACPR* — [resus.org.uk/respect](https://www.resus.org.uk/respect)
- Mental Capacity Act 2005 — UK statute; statutory principles and 2-stage capacity test.
- Fallowfield, L. & Jenkins, V. *Communicating sad, bad, and difficult news in medicine.* The Lancet, 2004.
- *R (Tracey) v Cambridge University Hospitals NHS Foundation Trust* [2014] EWCA Civ 822 — DNACPR discussion is required.

### Challenge 3 — Data Analytics

- Chicco & Jurman (2020) — see Chapter 06.
- Lundberg, S. M. & Lee, S. I. *A Unified Approach to Interpreting Model Predictions.* NeurIPS 2017 — the SHAP paper.
- Ribeiro, M. T., Singh, S. & Guestrin, C. *"Why Should I Trust You?": Explaining the Predictions of Any Classifier.* KDD 2016 — the LIME paper.

### Challenge 4 — Imaging Pneumonia

- Wang *et al.* (2017) — see Chapter 04.
- Rajpurkar *et al.* (2017) — see Chapter 04.
- He *et al.* (2016) — ResNet, see Chapter 04.
- Selvaraju *et al.* (2017) — Grad-CAM, see Chapter 04.
- Zech, J. R. *et al.* *Variable generalization performance of a deep learning model to detect pneumonia in chest radiographs.* PLOS Medicine, 2018 — the cross-site distribution-shift paper.

### Challenge 5 — Wearables

- Doherty, A. *et al.* *Large Scale Population Assessment of Physical Activity Using Wrist Worn Accelerometers: The UK Biobank Study.* PLoS ONE, 2017.
- Capture-24 dataset documentation — Oxford Wearables Group.
- Hildebrand, M. *et al.* *Age group comparability of raw accelerometer output from wrist- and hip-worn monitors.* Medicine & Science in Sports & Exercise, 2014 — the source of the cut-points.
- HL7 FHIR R4 specification — [hl7.org/fhir/R4](https://www.hl7.org/fhir/R4/).
- LOINC — [loinc.org](https://loinc.org/) — for activity, sleep, and physical-measurement codes.
- NHS England. *UK Core FHIR Implementation Guide* — for Wearables Challenge §10.E extension path.
- NHS Physical Activity Guidelines — [nhs.uk/live-well/exercise](https://www.nhs.uk/live-well/exercise) — the 150-minutes-MVPA-per-week reference used in the GPT narrative.

---

## NHS / regulatory references — central to multiple chapters

- General Medical Council. *Good Medical Practice* (2024).
- MHRA. *Software and AI as a Medical Device — change programme.*
- NHS England. *AI Ethics Initiative.*
- NHS England. *Equality and Health Inequalities Assessment (EHIA) framework.*
- NHS Digital. *DCB0129 — Clinical Risk Management for Health IT Systems.*
- NHS Digital. *DCB0160 — Application of risk management for health IT systems.*
- ICO. *Guidance on AI and data protection under UK GDPR.*
- EU AI Act (2024).
- *Care Quality Commission* — fundamental standards.

---

## A note on the references

This list is updated to v1.0 (Spring 2026). Some links may move; if you hit a dead one, the canonical names above will find the right paper or guidance via a normal search. **For NHS guidance specifically, always check the live NHS England / MHRA / GMC pages** rather than relying on cached references — clinical-AI guidance moves quickly and the current version is what governance committees apply.

---

*Appendix · Further reading · OCAI Booklet · Spring 2026 Edition*
