# Rationality-of-Large-language-models-
README: Testing Large Language Models on Legal and Rationality Questions
Overview
This repository contains the Python code used to evaluate multiple Large Language Models (LLMs) on a set of legal reasoning and rationality questions. The evaluation is conducted via API calls to the respective models without modifying any parameters to ensure consistency and comparability across models.

How It Works
The script sends a set of predefined legal and rationality questions to various LLMs.
API calls are made directly to the models without modifying any default parameters to ensure fair testing.
Responses are collected and stored for further analysis.
Setup Instructions
Requirements
Ensure you have Python installed along with the following dependencies:

bash
Copy
Edit
pip install openai anthropic transformers requests
API Configuration
Before running the script, configure API keys for each model in an .env file or directly within the script:

bash
Copy
Edit
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key
OTHER_MODEL_API_KEYS=your_other_model_keys
Alternatively, set environment variables in your terminal:

bash
Copy
Edit
export OPENAI_API_KEY="your_openai_api_key"
export ANTHROPIC_API_KEY="your_anthropic_api_key"
Running the Code
Execute the script by running:

bash
Copy
Edit
python test_llms.py
This will initiate API calls to the models and store the responses for further evaluation.

Models Tested
The following LLMs were tested using their respective APIs:

ChatGPT-4 (OpenAI)
ChatGPT-3.5 (OpenAI)
Gemini (Google DeepMind)
Claude 2 (Anthropic)
Llama 3 (Meta)
Mistral
Evaluation Criteria
Legal Reasoning: Ability to solve bar exam-style legal questions.
Rationality: Performance on reasoning-based cognitive tasks (e.g., Wason Selection Task, Conjunction Fallacy).
Notes
No model parameters were adjusted to maintain default settings during evaluation.
The dataset includes standardized legal and rationality questions to enable direct comparison between models.
Results & Analysis
Collected responses are stored in a structured format (.json or .csv) for statistical analysis. Future work may include further evaluation using statistical methods to compare model performance.

