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
