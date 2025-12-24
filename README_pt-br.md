# 👁️ FiscalLens AI

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![AI Engine](https://img.shields.io/badge/AI-OpenAI%20%2F%20Groq-green)
![Status](https://img.shields.io/badge/Status-Active%20Development-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> 🇺🇸 **[Read the English version here](README.md)**

**Motor de Extração de Dados Financeiros impulsionado por GenAI & LLMs.**
*Automatizando auditoria de notas fiscais, estruturando dados não-estruturados e detectando riscos de fraude em tempo real.*

---

## 🚀 O Problema
No setor financeiro corporativo, a **auditoria manual de notas fiscais** é lenta, cara e sujeita a falhas humanas. Empresas processam milhares de recibos de reembolso mensalmente, e **"micro-fraudes"** (como despesas pessoais escondidas em recibos corporativos) frequentemente passam despercebidas, causando vazamento de receita significativo.

## 💡 A Solução
**FiscalLens AI** é um pipeline inteligente que utiliza **Large Language Models (LLMs)** e **Prompt Engineering** para transformar texto bruto não-estruturado (saída de OCR) em dados JSON validados e prontos para auditoria.

Diferente de parsers tradicionais baseados em Regex, o FiscalLens entende o contexto, permitindo:
1.  **Extrair entidades** com robustez (Estabelecimento, Data, Total, Itens de Linha).
2.  **Analisar risco semântico** (ex: identificar "Bebida Alcoólica" ou "Tabaco" como itens não reembolsáveis).
3.  **Padronizar saídas** para integração direta com ERPs ou Dashboards.

---

## 🛠️ Tech Stack (Tecnologias)

* **Linguagem Core:** Python 3.x
* **Inteligência Artificial:** OpenAI API (GPT-3.5-Turbo / GPT-4)
* **Engenharia de Prompt:** Zero-Shot Extraction & Chain-of-Thought (CoT)
* **Gestão de Ambiente:** Python-Dotenv (Boas práticas de segurança)
* **Controle de Versão:** Git & GitHub

---

## ⚙️ Arquitetura

```mermaid
graph LR
    A[Texto Bruto da Nota] -->|Injeção de Contexto| B(Motor GenAI)
    B -->|Inferência Zero-Shot| C{Análise de Risco}
    C -->|Seguro| D[JSON Limpo]
    C -->|Item Suspeito| E[JSON com Alerta de Risco]
⚡ Funcionalidades Chave
[x] Extração Inteligente: Identifica Estabelecimento, Datas e Valores mesmo em formatos de texto bagunçados.

[x] Detecção de Fraude: Automaticamente sinaliza itens proibidos (Álcool, Tabaco, Entretenimento) baseando-se no contexto semântico.

[x] Saída Estruturada: Entrega formato JSON estrito pronto para inserção em banco de dados.

[x] Custo-Eficiente: Prompts otimizados para reduzir uso de tokens e latência.

💻 Instalação & Uso
1. Clone o repositório
Bash

git clone [https://github.com/matheuscassiano07/FiscalLens-AI.git](https://github.com/matheuscassiano07/FiscalLens-AI.git)
cd FiscalLens-AI
2. Configure o ambiente virtual
Bash

python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate
3. Instale as dependências
Bash

pip install -r requirements.txt
4. Configure as Chaves de Segurança
Crie um arquivo .env no diretório raiz e adicione sua API Key:

Snippet de código

OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxxxxxx
5. Execute o Motor
Bash

python core_engine.py
📊 Exemplo de Saída
Entrada (Texto Bruto):

Plaintext

RESTAURANTE DO ZÉ - 24/12/2025
Almoço Executivo.... R$ 45,00
Cerveja Pilsen...... R$ 12,00
Total: R$ 57,00
Saída do FiscalLens (JSON):

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
🗺️ Roadmap (Próximos Passos)
[ ] Integração com AWS Textract para processamento OCR de PDFs.

[ ] Pipeline de processamento em lote (batch) para auditoria de alto volume.

[ ] Visualização de Dashboard usando Streamlit.

[ ] Integração com Neo4j (Graph Database) para detecção de redes de fraude (Conexão com Projeto Argus).

🤝 Contato
Matheus Cassiano

https://www.linkedin.com/in/matheus-cassiano-/

https://github.com/matheuscassiano07

Projeto desenvolvido para fins educacionais e de portfólio, focando em Arquitetura Cloud & Segurança Financeira.