# 🧠 Rationality-of-Large-Language-Models  
### TriDoBench LLM Accuracy Evaluators (Law · Medical · LeetCode)

---

## 📌 Overview
This repository provides the **Python code, datasets, and evaluation scripts** for benchmarking Large Language Models (LLMs) across three complementary tracks:

1. **Law** — multiple-choice questions inspired by U.S. Bar exams and doctrinal reasoning.  
2. **Rationality** — cognitive and logical reasoning tasks (e.g., Wason Selection, Conjunction Fallacy, CRT).  
3. **Domain-Specific** — specialized knowledge in **medicine** (clinical reasoning MCQs) and **computer science** (algorithmic problem solving via LeetCode).  

The project is part of **TriDoBench**, a dissertation framework by *Dana Alsagheer (University of Houston)*, focused on evaluating **accuracy, consistency, and generalization** of LLMs beyond traditional benchmarks.

---

## ⚙️ How It Works
- Each evaluator script loads structured questions (Python dicts or PDFs).  
- Model queries are sent through their **official APIs**, using default parameters (e.g., temperature=1) for comparability.  
- Outputs are logged, compared against ground truth, and summarized in accuracy reports.  
- Multi-domain performance can be further analyzed using advanced metrics (TRCS, ICC, DSI, GCI).  

---

## 📁 Repository Layout
├─ medical_checking_llmaccuracy.py # Medical MCQ evaluator (dict-based questions)
├─ leetcode_checking_llmaccuracy.py # LeetCode auto-solver + scorer (Selenium)
├─ law_checking_llmaccuracy.py # (Optional) Legal reasoning evaluator
├─ checking_gptaccuracy (2).py # Generic rationality + law tester
├─ problems.txt # List of LeetCode problem URLs (one per line)
├─ data/
│ ├─ rationality.pdf # Rationality tasks (Wason, CRT, Conjunction Fallacy, etc.)
│ ├─ law.pdf # Legal reasoning (bar exam style)
│ ├─ law_core.pdf # Additional core legal questions
│ ├─ medical/ # Extra MCQ banks
│ └─ correlation/ # Cross-domain correlation analyses
└─ README.md

---

## 🧪 Example Dataset Format
All datasets follow a simple **dictionary schema** for direct API evaluation:

```python
{
  "question": "If a foreman is arrested ... will he prevail?",
  "A": "Option A",
  "B": "Option B",
  "C": "Option C",
  "D": "Option D",
  "correct": "A"
}
Running the Evaluators
1) Install Requirements
pip install openai anthropic mistralai google-genai selenium requests python-dotenv
2) Configure API Keys

Create a .env file:
