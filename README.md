# Rationality-of-Large-Language-Models

## README: Testing Large Language Models on Legal and Rationality Questions

### 🧠 Overview

This repository contains:
- Python scripts for evaluating the performance of LLMs
- Datasets formatted for direct testing of legal and rationality questions
- PDF files with well-structured multiple-choice questions suitable for LLM input
- Initial tools for analyzing model accuracy and consistency

---

### 📁 Included Files

- `Rationilty formatted .pdf`: Contains rationality tasks such as Wason Selection Task, Conjunction Fallacy, CRT.
- `___# Law Data___.pdf`: Contains legal reasoning questions drawn from Bar-style exams.
- `bartest core(law) .pdf`: Additional core legal test items.
- `checking_gptaccuracy (2).py`: Script to test LLMs on the above datasets.
- `corrlation`: Folder or file likely related to statistical correlation analysis (e.g., performance across domains).
- `README.md`: This documentation.

---



### 💡 Dataset Format

Questions are formatted in `.pdf` files using Python-style dictionaries for easy API-based LLM testing.

Example:

```python
{
    'question': (
        "A factory foreman was suspected of having murdered, for pay, the rival of a local union leader. ..."
    ),
    'A': "Option A",
    'B': "Option B",
    'C': "Option C",
    'D': "Option D",
    'correct': "A"
}

---
### Requirements
Install necessary dependencies:

bash
Copy
Edit
pip install openai anthropic transformers requests
Set your API keys in a .env file or use environment variables:

bash
Copy
Edit
export OPENAI_API_KEY="your_openai_api_key"
export ANTHROPIC_API_KEY="your_anthropic_api_key"
▶️ Running the Script
To run the evaluation:

bash
Copy
Edit
python checking_gptaccuracy\ \(2\).py
This script will:

Load the formatted questions

Send them to the specified LLM

Store the answers for later analysis
---

### 🤖 Models Tested
GPT-4 (OpenAI)

GPT-3.5 (OpenAI)

Claude 2 (Anthropic)

Gemini (Google DeepMind)

LLaMA 3 (Meta)

Mistral

### 📊 Evaluation Focus
Legal Reasoning: Bar-style legal logic and knowledge

Rationality: Cognitive logic and reasoning, including:

Wason Selection Task

Conjunction Fallacy

Base Rate Neglect

Cognitive Reflection Test (CRT)
