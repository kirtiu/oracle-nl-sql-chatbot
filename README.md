📘AI-Powered Oracle SQL Chatbot with Visualization

🧠 Overview

This project is a Streamlit-based AI chatbot that translates natural language (NL) queries into Oracle SQL statements, executes them securely, and visualizes the results. It integrates OpenAI for language understanding and Retrieval-Augmented Generation (RAG) to enhance SQL accuracy using schema metadata and business rules.

🚀 Features

Accepts natural language queries from users.
Uses OpenAI API to generate Oracle SQL statements.
Executes SQL queries securely using Oracle DB.
Displays results in tabular and graphical formats (bar, pie, line charts).
Provides natural language summaries of query results.
Integrates RAG to retrieve schema context and improve SQL generation.
Rejects unsafe queries (INSERT, UPDATE, DELETE).
Handles greetings and irrelevant inputs gracefully.

🏗️ Architecture

User → Streamlit UI → OpenAI API → Oracle DB → Results (Table + Charts + Summary)

🔄 Flow Summary

User submits a natural language query.
OpenAI generates SQL.
SQL is cleaned, secured, and validated.
Query is executed in Oracle DB.
Results are displayed with charts and summaries.
Errors and invalid inputs are handled gracefully.

🛠️ Setup Instructions

1. Clone the repository
2. Create and activate virtual environment
python -m venv venv
venv\Scripts\activate         # Windows
3. Install dependencies
pip install -r requirements.txt
4. Configure environment variables
Create a .env file in the root directory with:
OPENAI_API_KEY=your_openai_key
ORACLE_USER=your_db_user
ORACLE_PASSWORD=your_db_password
ORACLE_HOST=your_db_host
ORACLE_PORT=your_db_port
ORACLE_SID=your_db_sid
5. Run the chatbot
streamlit run app.py

📦 Libraries Used

streamlit – Interactive web app framework.
openai – GPT-based natural language processing.
cx_Oracle – Oracle DB connectivity.
pandas – Data manipulation and tabular display.
plotly – Interactive visualizations.
streamlit – Enhanced dashboard interactivity.
python-dotenv – Secure environment variable loading.


