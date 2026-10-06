# Hello-World Test Notebook — Outline

This is the cell-by-cell plan for `00_hello_world_test.ipynb`. Cowork (or any author) can build the actual `.ipynb` by following this outline literally — each entry below is one notebook cell, in order.

The test does five things, in order:

1. Confirms Python ≥ 3.10.
2. Imports every library the booklet uses.
3. Reads `OPENAI_API_KEY` from the environment and validates its format.
4. Makes a real (tiny) chat completion call to GPT-4o-mini.
5. Loads a small public HuggingFace dataset.

Total run time: ~5–10 seconds (after dependencies are installed).

---

## Cell 1 — Markdown — Title and welcome

```markdown
# Hello, world — booklet environment check

Run all cells (Run → Run All Cells, or Runtime → Run all in Colab).

This notebook performs five checks. If all five pass, your environment is
ready for the booklet. If any check fails, the cell will print a clear
message pointing to the most likely fix.

Estimated run time: 5–10 seconds.
```

---

## Cell 2 — Markdown — Step 1 / 5

```markdown
## Step 1 / 5 — Python version

The booklet requires Python 3.10 or higher. Most environments meet this by
default, but it's worth confirming.
```

---

## Cell 3 — Code — Python version check

```python
import sys

required = (3, 10)
actual = sys.version_info[:2]

print(f"Python version detected: {sys.version.split()[0]}")

assert actual >= required, (
    f"Python {required[0]}.{required[1]}+ required; you have {actual[0]}.{actual[1]}. "
    "Recreate your environment with a newer Python (see Section 0 setup guide)."
)

print("✓ Python version OK")
```

**Expected output**

```
Python version detected: 3.11.x
✓ Python version OK
```

---

## Cell 4 — Markdown — Step 2 / 5

```markdown
## Step 2 / 5 — Dependencies

We import every library the booklet uses. If any are missing, the cell
will report them and stop.
```

---

## Cell 5 — Code — Import all booklet dependencies

```python
required_modules = [
    ("openai", "OpenAI API client"),
    ("huggingface_hub", "HuggingFace Hub client"),
    ("datasets", "HuggingFace datasets"),
    ("transformers", "HuggingFace transformers"),
    ("sklearn", "scikit-learn"),
    ("shap", "SHAP explainability"),
    ("lime", "LIME explainability"),
    ("pandas", "pandas"),
    ("numpy", "NumPy"),
    ("matplotlib", "matplotlib"),
    ("ipywidgets", "ipywidgets"),
    ("PIL", "Pillow (image handling)"),
    ("torch", "PyTorch (Challenge 4)"),
    ("torchvision", "torchvision (Challenge 4)"),
]

missing = []
for mod_name, friendly_name in required_modules:
    try:
        __import__(mod_name)
        print(f"  ✓ {friendly_name}")
    except ImportError:
        missing.append((mod_name, friendly_name))
        print(f"  ✗ {friendly_name} — NOT installed")

if missing:
    print(
        "\nSome libraries are missing. Run this in a cell, then restart the kernel:\n"
        "    !pip install -r requirements.txt"
    )
    raise SystemExit("Stopping — install missing dependencies and re-run.")

print("\n✓ All dependencies present")
```

**Expected output**: each library shows ✓, ending in `✓ All dependencies present`.

---

## Cell 6 — Markdown — Step 3 / 5

```markdown
## Step 3 / 5 — OpenAI API key

We look for `OPENAI_API_KEY` in your environment. We do **not** print it —
ever. This cell only checks that it exists and that it has the expected
shape.
```

---

## Cell 7 — Code — Read and validate API key

```python
import os

# Colab convenience: pull from Colab secrets if available
try:
    from google.colab import userdata  # noqa: F401
    if "OPENAI_API_KEY" not in os.environ:
        os.environ["OPENAI_API_KEY"] = userdata.get("OPENAI_API_KEY") or ""
except ImportError:
    pass  # Not in Colab; assume environment variable is set directly

api_key = os.environ.get("OPENAI_API_KEY", "").strip()

if not api_key:
    print(
        "✗ OPENAI_API_KEY is not set.\n\n"
        "Most likely fix:\n"
        "  - Colab: add the key under the key icon in the left sidebar,\n"
        "    name OPENAI_API_KEY, toggle 'Notebook access' on.\n"
        "  - Local: export OPENAI_API_KEY='sk-...' in your shell, then\n"
        "    restart the kernel.\n"
        "  - Codespaces: add as a Codespace secret in GitHub settings,\n"
        "    then rebuild the container."
    )
    raise SystemExit("Stopping — set OPENAI_API_KEY and re-run.")

if not api_key.startswith("sk-"):
    print(
        "✗ OPENAI_API_KEY does not look right — it should start with 'sk-'.\n"
        "  Check you copied the full key without extra characters."
    )
    raise SystemExit("Stopping — fix the key and re-run.")

print(f"✓ OPENAI_API_KEY found (length {len(api_key)} chars, starts with sk-)")
```

**Expected output**

```
✓ OPENAI_API_KEY found (length 51 chars, starts with sk-)
```

(Length will vary by key format; anywhere in the 40–200 character range is normal.)

---

## Cell 8 — Markdown — Step 4 / 5

```markdown
## Step 4 / 5 — A real OpenAI call

We send a tiny prompt to GPT-4o-mini and print the reply. This costs a
fraction of a cent. If your billing isn't set up, this is where you'll
find out.
```

---

## Cell 9 — Code — Tiny OpenAI chat completion

```python
from openai import OpenAI, AuthenticationError, RateLimitError, APIConnectionError

client = OpenAI()  # Reads OPENAI_API_KEY from environment

try:
    response = client.chat.completions.create(
        model="gpt-4o-mini",
        max_tokens=20,
        messages=[
            {"role": "system", "content": "You are a clinical AI assistant."},
            {"role": "user", "content": "In one short sentence, what is sepsis?"},
        ],
    )
    reply = response.choices[0].message.content
    print(f"GPT-4o-mini says: {reply}")
    print("\n✓ OpenAI API call succeeded")

except AuthenticationError:
    print(
        "✗ Authentication failed. The API key was rejected.\n"
        "  - Check the key has no leading/trailing whitespace.\n"
        "  - Confirm a payment method is set up at platform.openai.com/billing."
    )
    raise SystemExit("Stopping — fix authentication and re-run.")

except RateLimitError:
    print(
        "✗ Rate limit hit. New OpenAI accounts have lower initial limits.\n"
        "  Wait 1–2 minutes and re-run. Limits raise automatically after\n"
        "  successful first billing."
    )
    raise SystemExit("Stopping — wait and re-run.")

except APIConnectionError:
    print(
        "✗ Could not reach OpenAI. Likely a network issue. Check your\n"
        "  connection and any corporate proxy or VPN settings."
    )
    raise SystemExit("Stopping — fix network and re-run.")
```

**Expected output**: a one-sentence definition of sepsis, then `✓ OpenAI API call succeeded`.

---

## Cell 10 — Markdown — Step 5 / 5

```markdown
## Step 5 / 5 — Load a public HuggingFace dataset

The booklet uses several open clinical datasets. We load a small one as a
sanity check. If HuggingFace is unavailable, we fall through to a CSV
fallback URL — exactly the pattern the rest of the booklet uses.
```

---

## Cell 11 — Code — Load a small public dataset, with fallback

```python
import pandas as pd

print("Attempting HuggingFace load: mstz/heart_failure ...")

try:
    from datasets import load_dataset
    ds = load_dataset("mstz/heart_failure", split="train")
    df = ds.to_pandas()
    source = "HuggingFace"
except Exception as e:
    print(f"  HuggingFace load failed ({type(e).__name__}). Falling back to CSV...")
    fallback_url = (
        "https://archive.ics.uci.edu/ml/machine-learning-databases/00519/"
        "heart_failure_clinical_records_dataset.csv"
    )
    df = pd.read_csv(fallback_url)
    source = "UCI fallback"

print(f"\nLoaded {len(df)} rows, {df.shape[1]} columns from: {source}")
print(f"First 3 column names: {list(df.columns[:3])}")
print("\n✓ Dataset load succeeded")
```

**Expected output**

```
Attempting HuggingFace load: mstz/heart_failure ...

Loaded 299 rows, 13 columns from: HuggingFace
First 3 column names: ['age', 'anaemia', 'creatinine_phosphokinase']

✓ Dataset load succeeded
```

(Or `from: UCI fallback` if HuggingFace is unreachable. Either is success.)

---

## Cell 12 — Markdown — All checks passed

```markdown
## ✓ All checks passed

Your environment is ready for the booklet.

**Next step**: open `../01_foundations/` and start with Section 1.

You won't need to run this notebook again unless something about your
environment changes — a new laptop, a new codespace, an expired API key.
```

---

## Cell 13 — Code — Final summary

```python
print("=" * 50)
print("ENVIRONMENT CHECK COMPLETE")
print("=" * 50)
print(f"Python:       {sys.version.split()[0]}")
print(f"OpenAI API:   ✓ working")
print(f"HuggingFace:  ✓ accessible")
print(f"Dependencies: ✓ all installed")
print("=" * 50)
print("\nReady for Section 1. Have fun.")
```

**Expected output**: a tidy summary block.

---

## Notes for the notebook author

A few things worth getting right when you build the actual `.ipynb`:

- **Cell metadata.** Set `"execution_count": null` on all code cells so the notebook ships with no stale outputs. Do not commit a notebook with execution counts or cached outputs — outputs from a previous run can leak (for example, a printed API response). Strip outputs before saving.
- **Kernel.** Ship with `python3` as the kernelspec. Don't pin to a Conda environment name; the booklet runs in many environments.
- **Imports at the top of each cell.** This notebook deliberately imports things in the cell where they're used, rather than once at the top. The reason: a beginner reading cell 7 should be able to see what `os.environ.get` needs, without scrolling back to a lost import block.
- **Error handling style.** Each step prints a specific, actionable message and then `raise SystemExit(...)`. The reader gets one clear instruction per failure, not a Python traceback. This pattern should be reused throughout the booklet.
- **Don't print the API key.** Anywhere. Not the first 4 chars, not the last 4 chars. Length is fine; content is not.
- **Leave the fallback path in.** The CSV fallback in Cell 11 is the same pattern used in every challenge that loads a HuggingFace dataset. The hello-world notebook is the right place to demonstrate it working.

---

*Hello-world test outline · Section 0 · OCAI Booklet · Spring 2026 Edition*
