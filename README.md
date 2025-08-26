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
.
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

yaml
Copy
Edit

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
▶️ Running the Evaluators
1) Install Requirements
bash
Copy
Edit
pip install openai anthropic mistralai google-genai selenium requests python-dotenv
2) Configure API Keys
Create a .env file:

ini
Copy
Edit
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key
MISTRAL_API_KEY=your_mistral_api_key
GEMINI_API_KEY=your_gemini_api_key
LLMAPI_KEY=your_llama_key
LEETCODE_USER=your_username
LEETCODE_PASS=your_password
3) Run Scripts
bash
Copy
Edit
# Rationality & Law
python checking_gptaccuracy.py

# Medical Track
python medical_checking_llmaccuracy.py

# LeetCode Track
python leetcode_checking_llmaccuracy.py
🤖 Models Supported
GPT-4, GPT-3.5 (OpenAI)

Claude 2/3 (Anthropic)

Gemini (Google DeepMind)

LLaMA-3 (Meta, via API)

Mistral (open-source API)

DeepSeek

📊 Evaluation Criteria
Law

Bar exam style multiple-choice accuracy.

Logical consistency across doctrinal reasoning tasks.

Rationality

Wason Selection Task → Logical rule following.

Conjunction Fallacy → Probabilistic reasoning.

Base Rate Neglect → Incorporation of statistical priors.

Cognitive Reflection Test (CRT) → Reflective vs. intuitive reasoning.

Domain-Specific

Medical → Clinical reasoning in echocardiography and ultrasound.

Computer Science → Algorithmic problem solving (LeetCode).

📊 Example Output
yaml
Copy
Edit
=== chp5 (Medical) ===
Q82: Pulse duration is affected by:…
  Claude  -> A  [correct]
  Gemini  -> A  [correct]
  Mistral -> C  [wrong]
  LLaMA   -> D  [wrong]

--- Accuracy Summary ---
Mistral   : 254/496 (51.2%)
DeepSeek  : 297/496 (59.9%)
Gemini    : 233/496 (47.0%)
LLaMA-3.2 : 155/496 (31.3%)
For LeetCode:

yaml
Copy
Edit
=== RESULTS ===
openai   : 78/100 passed (78.0%)
claude   : 65/100 passed (65.0%)
gemini   : 50/100 passed (50.0%)
🚀 Roadmap
 Add consistency metrics (TRCS, ICC).

 Add cross-domain generalization index (DSI, GCI).

 Expand rationality datasets (moral dilemmas, decision paradoxes).

 Unified CLI for model selection and output logging.

📚 Citation
If you use this toolkit, please cite:

Dana Alsagheer, TriDoBench: Auditing Consistency and Generalization in LLMs (PhD Dissertation, University of Houston, 2025).
