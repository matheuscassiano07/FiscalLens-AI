# 👁️ FiscalLens AI

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![AI Engine](https://img.shields.io/badge/AI-OpenAI%20%2F%20Groq-green)
![Status](https://img.shields.io/badge/Status-Active%20Development-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> 🇧🇷 **[Leia a versão em Português aqui](README_pt-br.md)**

**Financial Data Extraction Engine powered by GenAI & LLMs.**
*Automating invoice auditing, structuring unstructured data, and detecting fraud risks in real-time.*

---

## 🚀 The Problem
In the corporate financial sector, **manual invoice auditing** is slow, expensive, and prone to human error. Companies process thousands of reimbursement receipts monthly, and **"micro-frauds"** (like personal expenses hidden in corporate receipts) often slip through unnoticed, causing significant revenue leakage.

## 💡 The Solution
**FiscalLens AI** is an intelligent pipeline that leverages **Large Language Models (LLMs)** and **Prompt Engineering** to transform raw unstructured text (OCR output) into validated, audit-ready JSON data.

Unlike traditional Regex-based parsers, FiscalLens understands context, allowing it to:
1.  **Extract entities** robustly (Store, Date, Total, Line Items).
2.  **Analyze semantic risk** (e.g., identifying "Alcohol" or "Tobacco" as non-reimbursable items).
3.  **Standardize outputs** for direct integration with ERPs or Dashboards.

---

## 🛠️ Tech Stack

* **Core Language:** Python 3.x
* **Generative AI:** OpenAI API (GPT-3.5-Turbo / GPT-4)
* **Prompt Engineering:** Zero-Shot Extraction & Chain-of-Thought (CoT)
* **Environment Management:** Python-Dotenv (Security best practices)
* **Version Control:** Git & GitHub

---

## ⚙️ Architecture

```mermaid
graph LR
    A[Raw Invoice Text] -->|Context Injection| B(GenAI Engine)
    B -->|Zero-Shot Inference| C{Risk Analysis}
    C -->|Safe| D[Clean JSON]
    C -->|Suspicious Item| E[JSON with Risk_Flag]
⚡ Key Features
[x] Smart Extraction: Identifies Establishment, Dates, and Values even in messy text formats.

[x] Fraud Detection: Automatically flags prohibited items (Alcohol, Tobacco, Entertainment) based on semantic context.

[x] Structured Output: Delivers strict JSON format ready for database insertion.

[x] Cost-Efficient: Optimized prompts to reduce token usage and latency.

💻 Installation & Usage
1. Clone the repository
Bash

git clone https://github.com/matheuscassiano07/FiscalLens-AI.git
cd FiscalLens-AI
2. Set up the environment
Bash

python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate
3. Install dependencies
Bash

pip install -r requirements.txt
4. Configure Security keys
Create a .env file in the root directory and add your API Key:

Snippet de código

OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxxxxxx
5. Run the Engine
Bash

python core_engine.py
📊 Example Output
Input (Raw Text):

Plaintext

RESTAURANTE DO ZÉ - 24/12/2025
Almoço Executivo.... R$ 45,00
Cerveja Pilsen...... R$ 12,00
Total: R$ 57,00
FiscalLens Output (JSON):

JSON

{
  "establishment": "RESTAURANTE DO ZÉ",
  "date": "2025-12-24",
  "total_amount": 57.00,
  "items": [
    {"description": "Almoço Executivo", "value": 45.00},
    {"description": "Cerveja Pilsen", "value": 12.00}
  ],
  "risk_assessment": {
    "flagged": true,
    "reason": "Restricted item detected: Alcohol (Cerveja)"
  }
}
🗺️ Roadmap
[ ] Integration with AWS Textract for PDF OCR processing.

[ ] Batch processing pipeline for high-volume auditing.

[ ] Dashboard visualization using Streamlit.

[ ] Integration with Neo4j (Graph Database) for fraud ring detection (Project Argus connection).

🤝 Contact
Matheus Cassiano

https://linkedin.com/in/matheus-cassiano-/

https://github.com/matheuscassiano07

Project developed for educational and portfolio purposes, focusing on Cloud Architecture & Financial Security.