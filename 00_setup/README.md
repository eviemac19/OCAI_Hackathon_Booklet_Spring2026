# Section 0 — Setup and Resources

This is the most important section of the booklet. Once you've completed it, every other notebook will work first time. Skip it and you'll be debugging instead of learning.

Aim to spend **30–60 minutes** here. Once is enough — you don't need to repeat any of this.

---

## What you'll have when you finish

- An OpenAI API key, with a usage limit you've set deliberately.
- A working Python environment of your choice — Google Colab, local JupyterLab, or GitHub Codespaces.
- All the booklet's dependencies installed.
- A free HuggingFace account (no payment required).
- A passing hello-world test notebook that confirms everything is wired up correctly.

---

## Step 1 — Get an OpenAI API key

### Clarification first: API ≠ ChatGPT subscription

The booklet uses the OpenAI **API**, not ChatGPT. They are different products and they bill separately:

| | ChatGPT | OpenAI API |
| --- | --- | --- |
| Where | chat.openai.com | platform.openai.com |
| What it is | Consumer chat interface | Programmatic access for developers |
| Billing | Free or fixed monthly subscription | Pay-as-you-go, billed by token usage |
| What we use here | — | This is what the booklet uses throughout |

A ChatGPT Plus subscription does **not** include API access. You need a separate OpenAI **platform** account for the API. (You can sign up for the platform with the same email you use for ChatGPT — they just won't share billing.)

### Walkthrough

1. **Sign up at https://platform.openai.com**, or log in if you already have a platform account.
2. **Add a payment method** under *Settings → Billing*. The booklet's tasks are inexpensive (estimate below), but the platform requires a payment method on file before generating API keys.
3. **Set a usage limit** under *Settings → Limits*. We strongly recommend a hard monthly limit of **$10–15**. This is your safety rail: if a notebook misbehaves and accidentally calls the API in a loop, you cannot lose more than your limit.
4. **Generate an API key** under *Dashboard → API keys → Create new secret key*. Give it a recognisable name such as *OCAI booklet*.
5. **Copy the key immediately.** It is shown once. If you close the tab without copying, you cannot retrieve it — you have to make a new one.
6. **Store it like a password.** Never paste it into chat, never commit it to GitHub, never email it. Step 2 below covers safe storage for each environment.

### Indicative budget

Completing all five challenges using **GPT-4o-mini** (the model used throughout this booklet) and **TTS-1** for Challenge 2: approximately **$5–10 total**. Setting your hard limit at $10–15 leaves comfortable headroom without exposure.

> **Treat the API key like a hospital system password.** It has billing power. If you suspect it has leaked — say you've accidentally committed it to a public repo — revoke it immediately at *platform.openai.com/api-keys* and generate a new one.

---

## Step 2 — Choose your environment

You can run the booklet in one of three places. They are all valid; pick whichever fits your situation.

| Option | Best if you… | Persistence | Internet |
| --- | --- | --- | --- |
| **A. Google Colab** | …are new to Python and want zero install. | Resets between sessions; outputs save to Google Drive. | Required throughout. |
| **B. Local JupyterLab** | …prefer working offline and iterating quickly. | Fully persistent on your machine. | Only when calling APIs or downloading datasets. |
| **C. GitHub Codespaces** | …already use GitHub and want a cloud dev environment. | Persistent until you delete the codespace. | Required throughout. |

If you're not sure, choose **Option A — Google Colab**. It is the path of least resistance and works on any laptop with a browser.

### Option A — Google Colab (recommended for clinicians new to Python)

**What Google Colab is, in one paragraph.** Colab is a free Google service that lets you run Jupyter notebooks in your browser, on Google's machines — no Python installation, no terminal, no environment management. You upload (or open from GitHub) a notebook, click *Run*, and the cells execute on a Google cloud machine. When you're done, your changes save to your Google Drive. The booklet was designed with Colab as the default path because it removes every setup step a clinician new to Python would otherwise hit.

**Step 1 — Open Colab and sign in**

1. Go to **https://colab.research.google.com** and sign in with any Google account (the same one you use for Gmail or Drive is fine).
2. You will land on a blank Colab landing page with a *File* menu and a side-bar.

**Step 2 — Open a notebook from the booklet**

Three ways. Pick whichever matches how you got the booklet:

- *File → Upload notebook* — if you downloaded the booklet zip and have the `.ipynb` files locally. Drag and drop one in.
- *File → Open notebook → GitHub* — paste the URL of the booklet's GitHub repo (if your trainer or the booklet author has shared one).
- *File → Open notebook → Google Drive* — if you've already uploaded the booklet folder to your Drive.

Once a notebook is open, you'll see cells stacked vertically — markdown (text) cells with formatted prose, and code cells with grey backgrounds.

**Step 3 — Choose your runtime (CPU vs GPU)**

*Runtime → Change runtime type*. You'll see a dropdown:

- **CPU** is fine for *everything except Challenge 4 (Imaging)*. Use this by default.
- **T4 GPU** is the free GPU; switch to it for Challenge 4 only. Free-tier GPU has daily quotas — Colab will warn you if you're approaching them.
- **TPU** — not used by this booklet; ignore.

**Step 4 — How to actually run a cell**

Click into any cell. Then either:

- Press **Shift + Enter** (most common — runs the cell and moves to the next), or
- Click the **▶ Play** button that appears on the cell's left edge, or
- *Runtime → Run all* to run every cell in the notebook from top to bottom.

While a code cell is running, you'll see a spinner. When it finishes, the output appears in a box directly below the cell. *Errors are normal* — Python prints them in red and they don't break Colab; read the last few lines (the most informative part) and ask the booklet's mentor's notes section if you get stuck.

**Step 5 — Add your OpenAI key safely**

Colab provides a built-in **Secrets** manager (key icon in the left sidebar). Use it; never paste your key into a code cell.

1. Click the key icon in the left sidebar.
2. Click *Add new secret*.
3. **Name**: `OPENAI_API_KEY`
4. **Value**: paste your key (starts with `sk-...`).
5. Toggle **Notebook access** on for the booklet's notebooks.

The hello-world test notebook reads it with this snippet (you don't need to write the snippet — every booklet notebook includes one already):

```python
from google.colab import userdata
import os
os.environ["OPENAI_API_KEY"] = userdata.get("OPENAI_API_KEY")
```

**Step 6 — Save your work to Google Drive**

Colab notebooks save to *Playground mode* by default — your changes are lost when the tab closes. To save your edits:

- *File → Save a copy in Drive* — creates an editable copy in your Google Drive that auto-saves as you work.
- After that, your notebook lives in *Drive → Colab Notebooks/* by default. You can rename or move it like any Drive file.

### Mounting Google Drive — for files that take a long time to build

Some notebooks build large artefacts that take 5–10 minutes to construct (Challenge 1's FAISS index over MedRAG textbooks is the main one). If you don't save these to Drive, every Colab session has to rebuild them. Mount your Drive once, save the artefact there, and subsequent sessions reload in seconds.

```python
from google.colab import drive
drive.mount('/content/drive')

# Then save / load to a Drive path:
INDEX_PATH = '/content/drive/MyDrive/OCAI_Booklet/medrag_textbooks_faiss'
```

The first time you mount, Colab pops up an authorisation window — grant it once, and the path stays available for that session. Each notebook that benefits from this points it out where it matters.

### Things to know about Colab — the gotchas no-one warns you about

- **Idle timeout.** Sessions disconnect after roughly **90 minutes of inactivity**, and have a maximum runtime of **12 hours** even if active. Save your work to Drive often.
- **Package wipe on reset.** When a session resets, installed Python packages disappear. Every booklet notebook handles this with a `pip install -r requirements.txt` cell at the top — when you re-open after a break, just re-run that one cell.
- **Variable wipe on reset.** All variables in memory (`df`, trained models, computed results) also disappear on reset. To re-create them, re-run the cells that defined them, in order. The notebooks are written so this is always quick — *unless* the cell builds a large artefact (FAISS, model fine-tune), in which case the *Mounting Drive* section above is the answer.
- **GPU rate limits.** Free Colab gives you several hours of T4 GPU per day. If you exceed the quota, switch back to CPU (most notebooks work fine on CPU) or come back tomorrow.
- **When everything seems wrong.** *Runtime → Restart runtime* clears the Python state without wiping installed packages. *Runtime → Disconnect and delete runtime* gives you a completely fresh machine. If a notebook seems broken after a few changes, restart first; it solves more problems than people expect.

**Help from inside Colab.** *Help → Search code snippets* opens a useful side panel with copy-paste recipes for common tasks (mounting Drive, reading files, plotting). And every cell has a *? — Open in playground* button that lets you test a single cell without committing changes to your saved notebook.

### Option B — Local JupyterLab

You have two install paths. Either is fine.

**Path 1 — Anaconda (recommended for academics already using it)**

1. Download Anaconda Distribution from https://www.anaconda.com/download. Install with default settings.
2. Open *Anaconda Prompt* (Windows) or your terminal (macOS / Linux).
3. Create a clean environment for the booklet:
   ```bash
   conda create -n ocai python=3.11 -y
   conda activate ocai
   ```
4. Install the booklet's dependencies:
   ```bash
   pip install -r requirements.txt
   ```
5. Launch JupyterLab:
   ```bash
   jupyter lab
   ```

**Path 2 — uv (faster, newer; recommended if you're comfortable with the command line)**

1. Install uv:
   - macOS / Linux: `curl -LsSf https://astral.sh/uv/install.sh | sh`
   - Windows (PowerShell): `powershell -c "irm https://astral.sh/uv/install.ps1 | iex"`
2. Create a virtual environment and install:
   ```bash
   uv venv ocai-env --python 3.11
   source ocai-env/bin/activate    # macOS / Linux
   ocai-env\Scripts\activate       # Windows
   uv pip install -r requirements.txt
   ```
3. Launch JupyterLab:
   ```bash
   jupyter lab
   ```

**Setting your OpenAI key as an environment variable**

- **macOS / Linux**, in your terminal session:
  ```bash
  export OPENAI_API_KEY="sk-..."
  ```
  To make it permanent, add the line to `~/.zshrc` or `~/.bashrc`.
- **Windows**, in Command Prompt:
  ```bat
  setx OPENAI_API_KEY "sk-..."
  ```
  Close and reopen your terminal for it to take effect.

**Verify it's set**

```bash
echo $OPENAI_API_KEY     # macOS / Linux
echo %OPENAI_API_KEY%    # Windows
```

You should see your key. If you see nothing, the variable isn't set in this terminal.

### Option C — GitHub Codespaces

**Setup**

1. You'll need a GitHub account.
2. From the booklet's GitHub repository (or your fork of it), click *Code → Codespaces → Create codespace on main*.
3. Wait ~30 seconds for the codespace to spin up. It opens VS Code in your browser.
4. In the integrated terminal, install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
5. Open any `.ipynb` file. Codespaces will prompt you to install the Python and Jupyter extensions if they aren't already.

**Adding your OpenAI key as a Codespace secret**

1. Go to https://github.com/settings/codespaces.
2. Under *Codespace secrets*, click *New secret*.
3. **Name**: `OPENAI_API_KEY`. **Value**: paste your key.
4. Under *Repository access*, grant access to the booklet repository.
5. Restart your codespace (*Codespaces menu → Rebuild container*) for the secret to load.

The secret is automatically loaded as an environment variable. No code changes needed.

**Free-tier limits**

GitHub Codespaces provides 60 hours per month of free compute on individual accounts (subject to change — check current limits at https://github.com/features/codespaces). Sufficient for the booklet, but stop your codespace when you're not using it (*Codespaces menu → Stop codespace*).

---

## Step 3 — Install dependencies

The booklet uses a single `requirements.txt` file (in this folder). The exact install command depends on your environment:

- **Colab**: Each notebook starts with a `!pip install -r requirements.txt` cell. Just run it.
- **Local JupyterLab**: Run `pip install -r requirements.txt` (or `uv pip install -r requirements.txt`) in your activated environment, **before** launching JupyterLab.
- **Codespaces**: Run `pip install -r requirements.txt` in the integrated terminal.

The dependency file is reproduced at the end of this guide for reference.

> **Why we pin versions.** The packages used in this booklet evolve quickly, and small version mismatches between (for example) NumPy and SHAP can produce confusing errors. Pinning means everyone gets the same versions the curriculum was tested on. If a package fails to install, see *Troubleshooting* at the end.

---

## Step 4 — Set up HuggingFace

Most of the public datasets used in this booklet (`mstz/heart_failure`, the chest X-ray dataset for Challenge 4, etc.) can be loaded **without** a HuggingFace account. We still recommend creating one — it's free, takes a minute, and avoids rate-limit errors when datasets are popular.

1. Sign up at https://huggingface.co (free).
2. Go to *Profile → Settings → Access Tokens → New token*.
3. **Name**: `ocai-booklet-read`. **Type**: *Read*.
4. Copy the token.
5. Set it as an environment variable named `HF_TOKEN`, in the same way you set `OPENAI_API_KEY` for your environment.

> **Network resilience.** Every HuggingFace dataset load in the booklet has a CSV/UCI fallback URL. If HuggingFace is down or you can't authenticate, the notebooks will fall through to the fallback. You will not get stuck.

---

## Step 5 — Run the hello-world test

Open `00_hello_world_test.ipynb` in this folder and run all cells (in JupyterLab: *Run → Run All Cells*; in Colab: *Runtime → Run all*).

The test does five things, in order:

1. Confirms your Python version is 3.10 or higher.
2. Imports every library the booklet uses, and reports any that are missing.
3. Reads `OPENAI_API_KEY` from your environment and validates its format.
4. Makes a tiny real call to GPT-4o-mini and prints the response.
5. Loads a small public HuggingFace dataset and shows its shape.

If all five steps pass, you'll see a clear success message at the bottom and you're ready for Section 1.

If any step fails, the test prints a specific message pointing to the most likely fix. The most common issues are:

- **`OPENAI_API_KEY` not found** → you set the variable in a different terminal session, or you didn't restart your environment after setting it.
- **Authentication error from OpenAI** → the key was copied with a leading or trailing space, or you set the key but haven't added a payment method on the platform yet.
- **Module not found** → the install cell didn't run, or you ran it in a different environment than the one currently active.
- **HuggingFace timeout** → unstable network. The test will fall back to a CSV URL automatically; if that also fails, retry once.

---

## You're ready

If the hello-world test passes, you have everything you need. Move on to **Section 1 — Foundations of AI** (`../01_foundations/`).

You will not need to come back to this section unless your environment changes (new laptop, new Codespace, expired key). Bookmark it just in case.

---

## Appendix — `requirements.txt` reference

For convenience, the dependencies used by the booklet are listed below. The canonical copy is in `requirements.txt` in this folder.

```
# OpenAI API client — booklet uses v1.x SDK syntax throughout
openai>=1.40.0,<2.0.0

# HuggingFace ecosystem
huggingface_hub>=0.23.0,<1.0.0
datasets>=2.20.0,<4.0.0
transformers>=4.42.0,<5.0.0

# ML stack (Challenge 3 and beyond)
scikit-learn>=1.3.0,<2.0.0
shap>=0.45.0,<1.0.0
lime>=0.2.0.1,<1.0.0

# Data and viz
pandas>=2.0.0,<3.0.0
numpy>=1.24.0,<2.2.0
matplotlib>=3.7.0,<4.0.0

# Notebook widgets (Challenge 3 interactive patient demo)
ipywidgets>=8.0.0,<9.0.0

# Image handling (Challenge 4 — chest X-ray)
Pillow>=10.0.0,<12.0.0
torch>=2.0.0,<3.0.0
torchvision>=0.15.0,<1.0.0
```

---

## Troubleshooting cheat sheet

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| `ModuleNotFoundError: No module named 'openai'` | The install cell didn't run, or you have multiple Python environments. | Re-run the install cell. Verify you're in the right environment with `which python` (macOS / Linux) or `where python` (Windows). |
| `openai.AuthenticationError` | API key wrong, missing, or no payment method on file. | Re-check the key has no whitespace; confirm at platform.openai.com that billing is set up. |
| `openai.RateLimitError` | Hit per-minute or per-day limit on a new account. | Wait a few minutes and retry. New accounts have lower initial limits which raise after first successful billing. |
| `KeyError: 'OPENAI_API_KEY'` in Colab | Secret toggle for *Notebook access* is off. | Click the key icon → toggle on for the relevant secret. |
| `huggingface_hub.errors.HfHubHTTPError` | HF auth or rate limit. | The notebook will fall through to a CSV fallback. If both fail, retry; if persistent, set `HF_TOKEN` as in Step 4. |
| LIME or SHAP installation hangs in Colab | Cold-start install of compiled deps. | Wait — first install can take 60–90 seconds. Subsequent runs are instant. |
| `numpy.dtype size changed` warnings | Version mismatch between NumPy and a library compiled against a different NumPy ABI. | Restart the kernel after `pip install`. If it persists, run `pip install --force-reinstall numpy`. |

If your problem isn't on this list, see the troubleshooting section in the relevant challenge notebook, or write to **events@clinicalaipartners.org**.

---

*Section 0 · OCAI Booklet · Spring 2026 Edition*
