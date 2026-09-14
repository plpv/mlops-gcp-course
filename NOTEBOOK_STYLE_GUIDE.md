# Notebook Style Guide — MLOps Introductory Course on GCP

> Reference this guide when creating or updating lab notebooks to ensure
> consistency across all sessions. The Lab 01 (MLflow) notebook serves as
> the canonical example.

---

## 1 · File Naming

```
lab{NN}_{short_topic_with_underscores}.ipynb
lab{NN}_{short_topic_with_underscores}_solution.ipynb
```

| Lab | Student file | Solution file |
|-----|-------------|---------------|
| 1 | `lab01_mlflow_experiment_tracking.ipynb` | `lab01_mlflow_experiment_tracking_solution.ipynb` |
| 2 | `lab02_vertex_ai_experiments.ipynb` | `lab02_vertex_ai_experiments_solution.ipynb` |
| 3 | `lab03_model_endpoints.ipynb` | `lab03_model_endpoints_solution.ipynb` |
| … | … | … |

Rules:
- Always two-digit lab number (`01`, `02`, …).
- Lowercase, underscores only, no spaces.
- The topic should be 2–4 words max.

---

## 2 · Notebook Header (first cell)

Every notebook starts with the **same** markdown cell. Copy-paste and change only the title and duration.

```markdown
<!-- ============================================================ -->
<!-- NOTEBOOK HEADER — MLOps Introductory Course on GCP           -->
<!-- ============================================================ -->

<div style="border-bottom: 3px solid #4285F4; padding-bottom: 12px; margin-bottom: 20px;">

<div style="display: flex; align-items: center; justify-content: space-between;">
  <div>
    <img src="https://www.isae-supaero.fr/wp-content/uploads/2025/03/logo.svg" width="180">
  </div>
  <div style="text-align: right;">
    <img src="https://www.headmind.com/wp-content/uploads/2024/01/logo_dark.png" width="140">
  </div>
</div>

# Lab {NN} — {Title}

**Course:** MLOps Introductory Course on GCP · M2 Data Science · ISAE-SUPAERO
**Lab created by:** Headmind Partners AI & Blockchain
**Estimated duration:** ~{X}h{YY}

</div>
```

For **solution** notebooks, append ` — ✅ Solution` to the title:

```markdown
# Lab {NN} — {Title} — ✅ Solution
```

---

## 3 · Overview (second cell)

Immediately after the header, include one markdown cell with:

1. **Business / technical context** — 2–3 sentences explaining _why_ this topic matters.
2. **Learning Objectives** — A numbered list of 4–6 concrete skills the student will acquire. Start each with a verb: "Launch…", "Log…", "Compare…", "Deploy…".
3. **Notebook Structure** — A table mapping section numbers to titles and one-line focus descriptions.
4. **How to Read This Notebook** — The legend below (keep identical across all labs).

```markdown
### How to Read This Notebook

- **`# TODO`** — Code you need to write. Look for the `######` delimiters.
- **`✏️ Question`** — A conceptual question. Write your answer in the markdown cell below it.
- Cells **without** a TODO are provided — read them, run them, and make sure you understand them.
- Documentation links are provided in 📖 callouts whenever a new API is introduced.
```

---

## 4 · Section Structure

### Section dividers

Each major section starts with a markdown cell:

```markdown
---
## {N} · {Section Title}
```

- Use a `---` horizontal rule **before** each top-level section to create a visual break.
- Number sections starting from `0` (Setup) through `N` (last section).
- Use the `·` (middle dot) separator: `## 3 · Model Registry`.

### Subsections

```markdown
### 3.1 Subsection title
```

- Use `###` for subsections, numbered `{section}.{sub}`.
- No `---` before subsections.

---

## 5 · Setup Section (Section 0)

Every notebook should have:

```
## 0 · Setup
### 0.1 Install dependencies       → %pip install -r requirements.txt -q
### 0.2 Imports                     → All imports in one cell, grouped logically
### 0.3 Configuration / Connection  → Constants, API keys, tracking URIs, etc.
```

### Import cell conventions

```python
import pickle
import warnings

import numpy as np
import pandas as pd
# ... more third-party libs ...

from sklearn.ensemble import RandomForestClassifier
# ... sklearn imports ...

import mlflow                      # or google.cloud, etc.
from mlflow import MlflowClient

warnings.filterwarnings("ignore", category=FutureWarning)
pd.set_option("display.max_columns", 50)

# ── Constants ──
RANDOM_STATE = 42
PROJECT_ID = "your-project-id"     # GCP-specific if needed

print(f"MLflow version: {mlflow.__version__}")
```

Group imports by: stdlib → third-party → domain-specific (sklearn, mlflow, vertex, etc.).
Define **all constants** (random seeds, split ratios, project IDs) at the top as uppercase variables.

---

## 6 · TODO Blocks (Code Exercises)

### Format

```python
##############################  TODO  ##############################
# Brief instruction telling the student WHAT to do, not HOW.
# If the API is new, add a hint or point to the 📖 docs callout above.
variable = ...  # TODO
####################################################################
```

Rules:
- Always use the exact `######  TODO  ######` banner (30 `#` + 2 spaces + "TODO" + 2 spaces + 30 `#`).
- Place `# TODO` inline on the line(s) the student needs to fill in.
- Use `...` (Ellipsis) as the placeholder, not `""`, `0`, or `None` (unless the default matters).
- Keep the block short: 1–6 lines of student code max.
- Below the `####` closing line, include validation / print statements so students get immediate feedback.

### Do vs. Don't

| ✅ Good TODO | ❌ Bad TODO |
|---|---|
| Asks the student to write a function call using a documented API | Asks the student to copy-paste a list of column names |
| Has one clear objective | Combines 3 unrelated tasks in one block |
| Provides inline hints or links to docs | Gives no context, student has to guess the syntax |
| Has a print/assert right after to confirm success | No feedback — student doesn't know if it worked |

### Difficulty guidance

The TODOs should test **understanding of the lab topic** (MLflow, Vertex AI, etc.), not general Python fluency. If the exercise is standard data science (e.g., one-hot encoding, train/test split), make it quick. Save complexity for the MLOps-specific code.

---

## 7 · Questions (Conceptual Exercises)

### Format

A question is **always** two consecutive markdown cells:

```markdown
**✏️ Question {N} — {Short title}**

a) First sub-question
b) Second sub-question
```

```markdown
---
*Your answer:*



---
```

Rules:
- Number questions sequentially across the whole notebook: Q1, Q2, Q3…
- Give each question a short descriptive title (e.g., "Class imbalance", "Train/Val/Test").
- Use `a)`, `b)`, `c)` sub-parts to structure multi-part questions.
- Keep to 2–3 sub-parts max.
- The answer cell uses `*Your answer:*` in italics (student version) or `*✅ Solution:*` (solution version).

### Solution version

```markdown
---
*✅ Solution:*

a) The dataset is **moderately imbalanced**: ~70% class 0, ~30% class 1.

b) The classifier favors the majority class...

---
```

### What makes a good question

| ✅ Good | ❌ Avoid |
|---|---|
| Tests understanding of the MLOps concept being taught | Tests general ML theory unrelated to the lab |
| Connects to what the student just coded | Is purely theoretical with no link to the notebook |
| Can be answered in 2–4 sentences | Requires a full essay |
| Has a clear expected answer | Is so open-ended that any answer works |

---

## 8 · Documentation Callouts

When introducing a new library, function, or concept for the first time, add a callout:

```markdown
> 📖 **Docs:** [Function name](https://link.to/docs)
```

For multiple related links:

```markdown
> 📖 **Key MLflow functions:**
> - [`mlflow.log_param()`](https://link)
> - [`mlflow.log_metric()`](https://link)
> - [`mlflow.sklearn.log_model()`](https://link)
```

For practical tips:

```markdown
> 💡 **Tip:** After running the cell, go to the MLflow UI and click Compare.
```

Use sparingly — one callout per new concept, not per cell.

---

## 9 · Summary Section (last cell)

End every notebook with:

```markdown
---
## Summary

In this lab, you learned to:

| Step | What you did | Tool / Feature used |
|------|-------------|---------------------|
| Setup | ... | ... |
| ... | ... | ... |

**Next lab:** Brief teaser of what's coming next.
```

The summary table should mirror the "Notebook Structure" table from the overview, but now phrased as accomplishments. The "Next lab" teaser gives continuity.

---

## 10 · Visual & Formatting Rules

### Plots

- Always include `plt.title(...)` and `plt.tight_layout()`.
- Use a consistent color palette: `#4285F4` (Google blue), `#EA4335` (red), `#FBBC04` (yellow), `#34A853` (green) — or `"coolwarm"` / `"Blues"` colormaps.
- Always `plt.show()` explicitly (don't rely on notebook auto-display).

### Print statements

- After every TODO, include a print that confirms success:
  ```python
  print(f"Train: {X_train.shape[0]} samples  |  Test: {X_test.shape[0]} samples")
  ```
- Use `✅` for success confirmations in provided cells:
  ```python
  print("✅ Model logged to MLflow.")
  ```

### Code cells without TODOs

- Add a brief comment at the top explaining what the cell does.
- Keep cells short (< 20 lines). If longer, split into logical pieces.

### Markdown formatting

- Use **bold** for key terms on first use.
- Use `inline code` for variable names, function names, file paths.
- Avoid raw HTML except in the header cell.
- No emojis in body text except the three standard markers: `✏️` (question), `📖` (docs), `💡` (tip), `✅` (success/solution).

---

## 11 · Solution Notebook Differences

The solution notebook is **structurally identical** to the student version. The only differences:

1. **Title** has ` — ✅ Solution` appended.
2. **TODO code cells** are replaced with completed code, prefixed with `# ✅ SOLUTION`.
3. **Answer cells** have `*✅ Solution:*` instead of `*Your answer:*`, with the answer filled in.

Everything else (markdown explanations, provided cells, doc callouts) stays identical.

### Building solutions programmatically

You can write a script that copies the student notebook and replaces specific cells by index or by searching for marker strings (`"# TODO"`, `"*Your answer:*"`). See the Lab 01 build script for reference.

---

## 12 · Checklist Before Publishing a Notebook

- [ ] File name follows `lab{NN}_{topic}.ipynb` convention
- [ ] Header cell has both logos, correct lab number, title, and duration
- [ ] Overview has context, learning objectives, structure table, and legend
- [ ] Sections numbered from 0 (Setup) with `---` dividers
- [ ] Section 0 has install, imports, and configuration
- [ ] Every TODO uses the `######  TODO  ######` banner
- [ ] Every TODO has a print/assert for feedback
- [ ] Every question uses `✏️ Question {N} — {Title}` format
- [ ] Every new API has a `📖 Docs:` callout with a working link
- [ ] Ends with a Summary table and "Next lab" teaser
- [ ] No unused imports
- [ ] No hardcoded credentials or project IDs (use `"your-project-id"` placeholder)
- [ ] Python version not mentioned (handled by requirements.txt)
- [ ] Solution notebook has all TODOs filled and all answers provided
- [ ] Both notebooks have the same number and order of cells
