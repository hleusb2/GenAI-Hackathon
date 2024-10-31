# 🚀 Generative AI Chatbot for Healthcare Device Work Orders

Welcome to the **Generative AI Chatbot for Healthcare Device Work Orders**! This project, developed as part of the Databricks Generative AI World Cup Hackathon 2024, enables a seamless, interactive query experience for healthcare work order data using **Retrieval-Augmented Generation (RAG)**. By combining natural language processing with robust SQL querying, this chatbot empowers users to gain actionable insights from complex data without needing SQL expertise.

## 🌟 Project Overview

Our chatbot is designed to answer complex queries on healthcare device work orders, enabling non-technical PIT team members to retrieve insights directly from structured data in the Databricks Unity Catalog. This project utilizes RAG to offer:
- Accurate responses by fetching relevant data prior to response generation
- Reliable, deterministic answers that support PIT team decisions
- Quick access to critical information on device status, escalations, technician activity, and more.

### Key Features
- **Natural Language Queries**: Users can query work orders with questions like "Show all closed work orders with part consumption 607301000."
- **RAG-Enhanced Response Accuracy**: Ensures responses are rooted in relevant, up-to-date data.
- **Chain of Agents**: Handles complex, structured SQL responses and scales with ease.

## 🏛️ Architecture Design

The architecture employs a high-level RAG workflow:
1. **Data Ingestion & Storage**: Salesforce API data is ingested and managed within Databricks Unity Catalog, ensuring data is readily available and updated.
2. **Data Retrieval Layer**: Our retrieval phase identifies and fetches the most relevant records, ensuring each response is grounded in factual, specific information.
3. **LLM Layer**: An LLM interprets user input and translates it into SQL. Leveraging the RAG approach, it generates responses only after retrieving data.
4. **Chain of Agents**: The chatbot directs queries to specialized SQL functions for high precision, enabling it to handle requests like “Show me all open work orders escalated for over 14 days.”

### Tech Stack
- **Languages**: Python, SQL
- **Frameworks**: Databricks Unity Catalog, TensorFlow/PyTorch (LLM model)
- **Tools**: Databricks, SQL functions, RAG-specific configurations
- **Cloud**: Databricks Cloud and integration with Salesforce API

## 📊 Data Collection and Training

We utilized a dataset comprising **36,280 records** of healthcare device work orders, sourced from Salesforce API and stored in the Databricks Unity Catalog. Key data metrics include:
- **Unique Work Orders**: 32,249
- **Closed Work Orders**: 27,548
- **Escalated Work Orders**: 3,969
- **Technician Mentions**: 29,513

Our RAG model was trained with **supervised learning techniques**, optimizing for deterministic SQL output. By focusing on recall, latency, and response consistency, the model is configured for accurate query handling in real-time.

### Performance Metrics
- **Accuracy**: 96% on commonly queried terms
- **Average Response Time**: Under 2 seconds
- **Consistency**: Deterministic SQL response

## 🔍 Model and Chatbot Use Cases

Our chatbot handles diverse user queries, including:
- **Escalation Tracking**: "Show me all open/assigned work orders escalated for over 14 days."
- **Technician Activity**: "Show all my escalated work orders where the technician has replied."
- **Work Order Status**: "List all open work orders without an assigned technician."

### RAG-Enabled Workflow
Each query follows the RAG process:
1. **Retrieve**: Relevant data is retrieved based on the question context.
2. **Generate**: The LLM processes the query and formats it as a SQL query.
3. **Respond**: SQL results are returned as structured answers in natural language.

## 🔧 Installation and Usage

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/yourusername/generative-ai-chatbot.git
    cd generative-ai-chatbot
    ```

2. **Configure RAG Chain**:
   Ensure that `rag_chain_config.yaml` is configured with the appropriate parameters.

3. **Run Data Preparation**:
   ```python
   python 01-Data-Preparation.py
   ```

4. **Deploy Chatbot Model**:
   ```python
   python 02-Deploy-RAG-Chatbot-Model_WO.py
   ```

5. **Launch Chatbot**:
   Run the primary `chain.py` script to initialize the RAG-based chatbot for querying:
   ```python
   python chain.py
   ```

6. **Query Examples**:
   - "What is the average de-escalation time for work orders?"
   - "Show all closed work orders escalated to [Technician Name] for the past three months."

## 🚀 Future Scope

Our long-term vision includes:
- **Enhanced SQL Precision**: Expanding the chain of agents to cover increasingly complex queries.
- **Advanced Query Optimization**: Implementing caching and indexing for high-demand queries.
- **Cross-Domain Expansion**: Adapting the chatbot to manage similar query workflows in other data-heavy industries.
- **Personalized User Experience**: Adding user-specific history and preferences to improve response time and relevance.

## 📁 Repository Structure

```plaintext
├── data
│   ├── raw
│   └── processed
├── config
│   └── rag_chain_config.yaml
├── notebooks
│   ├── Data-Preparation.ipynb
│   └── Model-Deployment.ipynb
├── src
│   ├── data_processing.py
│   ├── deploy_chatbot.py
│   └── chain.py
├── README.md
```

## 👥 Contributors
- **Hang Le** - Chatbot Design, Model Training, Codebase Documentation
- **Brian Zavareh** - Data Processing
