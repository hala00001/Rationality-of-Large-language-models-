# Rationality-of-Large-Language-Models

## README: Testing Large Language Models on Legal and Rationality Questions

---

## 🧠 Overview

This repository contains the Python code and structured datasets used to evaluate multiple Large Language Models (LLMs) on a set of **legal reasoning** and **rationality** questions. The evaluation is conducted via API calls to the respective models, using **default parameters** to ensure consistency and comparability across models.

---

## ⚙️ How It Works

- The script sends a predefined set of legal and rationality questions to various LLMs.
- API calls are made directly, without modifying model settings (e.g., temperature, top_p).
- Model responses are collected and stored for analysis.

---
## 📁 Included Files

Rationilty formatted .pdf: Contains rationality tasks such as Wason Selection Task, Conjunction Fallacy, CRT.

___# Law Data___.pdf: Contains legal reasoning questions drawn from Bar-style exams.

bartest core(law) .pdf: Additional core legal test items.

checking_gptaccuracy (2).py: Script to test LLMs on the above datasets.


corrlation: Folder or file likely related to statistical correlation analysis (e.g., performance across domains).

README.md: This documentation.

## 🔧 Setup Instructions

### Requirements

Ensure you have Python installed, and run the following to install the necessary dependencies:

```bash
pip install openai anthropic transformers requests
API Configuration
You can configure your API keys by:

Creating a .env file:

bash
Copy
Edit
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key
Or exporting them directly in your terminal:

bash
Copy
Edit
export OPENAI_API_KEY="your_openai_api_key"
export ANTHROPIC_API_KEY="your_anthropic_api_key"
▶️ Running the Code
To execute the evaluation, run:

bash
Copy
Edit
python test_llms.py
This will initiate API calls to all configured models and save their responses to local files for further evaluation.

🤖 Models Tested
The following LLMs were tested using their respective APIs:

ChatGPT-4 (OpenAI)

ChatGPT-3.5 (OpenAI)

Gemini (Google DeepMind)

Claude 2 (Anthropic)

LLaMA 3 (Meta)

Mistral

📊 Evaluation Criteria
Legal Reasoning:
Ability to correctly answer multiple-choice questions based on U.S. bar exam formats.

Rationality:
Performance on standardized reasoning-based cognitive tasks, including:

Wason Selection Task – Logical rule evaluation.

Conjunction Fallacy – Probabilistic reasoning under uncertainty.

Base Rate Neglect – Incorporating statistical base rates in judgments.

Cognitive Reflection Test (CRT) – Reflective vs. intuitive reasoning.

📁 Dataset Format
All questions are formatted as Python dictionaries to be directly used in API calls. Example format:

python
Copy
Edit
{
    "question": "If a foreman is arrested ... will he prevail?",
    "A": "Option A",
    "B": "Option B",
    "C": "Option C",
    "D": "Option D",
    "correct": "A"
}
Questions are available in .pdf format under the dataset directory and are designed for compatibility with any LLM testing pipeline.

#############################
# TriDoBench LLM Accuracy Evaluators (Law · Medical · LeetCode)

A lightweight, reproducible toolkit to **evaluate large language models (LLMs)** on three tracks:

- **Law** — multiple-choice/short-answer questions (add your dataset file; same schema as Medical).
- **Medical** — echo/ultrasound and cardiology-focused MCQs (already included).
- **LeetCode** — browser-driven solving of Hard problems with Selenium and pass/fail scoring.

This repo is part of Dana Alsagheer’s dissertation work on **consistency, reliability, and cross-domain generalization** of LLMs (TriDoBench). It provides clean scripts and data structures you can run locally or on Colab to get **per-model accuracy** and raw run logs.


## Repository Layout

.
├─ medical_checking_llmaccuracy.py # Medical MCQ evaluator (dict-based questions)
├─ leetcode_checking_llmaccuracy.py # LeetCode auto-solver + scorer (Selenium)
├─ problems.txt # List of LeetCode problem URLs (one per line)
├─ law_checking_llmaccuracy.py # (Optional) Law evaluator – add your file here
├─ data/
│ ├─ law/ # (Optional) Your law MCQ JSON/CSV lives here
│ └─ medical/ # (Optional) extra medical question banks
└─ README.md

pgsql
Copy
Edit


## What’s Inside

### Medical evaluator
- Each chapter `chpN` is a **list of dicts** with keys `number`, `question`, options (`A`–`D`), and `correct` (gold label).
- The script can loop questions, query one or more models, and print run-by-run correctness + summary accuracy.
- Model endpoints already scaffolded: **Llama (llmapi)**, **Gemini**, **Mistral**, **Claude**, **OpenAI**.

**Example item (schema):**
```python
{
  "number": 1,
  "question": "The speed of sound in tissues is:",
  "A": "Roughly 1540 m/s",
  "B": "Roughly 1540 km/s",
  "C": "Roughly 1540 cm/s",
  "D": "Roughly 1540 m/min",
  "correct": "A"
}
Example output (truncated):

yaml
Copy
Edit
=== chp5 ===
Q82: Pulse duration is affected by:…
  Claude  -> A  [correct]
...
Mistral  : 254/496 correct  (51.21%)
DeepSeek : 297/496 correct  (59.88%)
Gemini   : 233/496 correct  (46.98%)
Llama-3.2: 155/496 correct  (31.25%)
LeetCode evaluator
Uses Selenium + Chrome to navigate each URL from problems.txt, scrape description + starter code, call a selected model adapter, paste the answer into the editor, run tests, and record Accepted vs Wrong Answer.

Toggle models via boolean flags (OpenAI, DeepSeek, Claude, Mistral, Gemini, Llama) and pass your API keys through environment variables.

Prints a final score table like: openai : 78/100 passed (78.0%).

Example problems.txt:

ruby
Copy
Edit
https://leetcode.com/problems/median-of-two-sorted-arrays/
https://leetcode.com/problems/regular-expression-matching/
...

