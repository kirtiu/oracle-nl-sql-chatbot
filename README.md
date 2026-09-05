# 🗄️ Oracle NL-SQL Chatbot

Convert natural language to Oracle SQL. Ask questions, get data visualizations.

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-Latest-red)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o-black)
![Oracle](https://img.shields.io/badge/Oracle-Database-red)

---

## ✨ Features

- 💬 Natural Language to SQL queries
- 🔒 Safe execution (blocks INSERT, UPDATE, DELETE)
- 🤖 Intent classification (greetings, questions, queries)
- 📊 Auto-generates charts (bar, pie, line)
- 🧠 RAG engine for accurate SQL generation
- ✅ Result explanations in plain English

---

## 📋 Prerequisites

- Python 3.8+
- Oracle Database access
- OpenAI API key

---

## ⚙️ Installation

1. **Clone**
   `ash
   git clone https://github.com/kirtiu/oracle-nl-sql-chatbot.git
   cd oracle-nl-sql-chatbot
   `

2. **Virtual Environment**
   `ash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   `

3. **Install Dependencies**
   `ash
   pip install -r requirements.txt
   `

4. **Setup .env**
   `env
   OPENAI_API_KEY=sk-your-key
   ORACLE_USER=your_user
   ORACLE_PASSWORD=your_password
   ORACLE_HOST=your_host
   ORACLE_PORT=1521
   ORACLE_SID=your_sid
   `

5. **Run**
   `ash
   streamlit run app.py
   `

Access at: **http://localhost:8501**

---

## 🎯 How to Use

### Ask Questions
`
"How many employees in Sales?"
"Show salary by department"
"Compare expenses by quarter"
`

### Result
- SQL query displayed
- Data table shown
- Auto-generated chart
- AI explanation provided

---

## 📂 Project Files

- **app.py** - Main Streamlit application
- **db.py** - Oracle database connection
- **openai.py** - AI & intent classification
- **rag_engine.py** - Vector search (FAISS)
- **visualizer.py** - Chart generation
- **oracle_chatbot_knowledge.txt** - Knowledge base
- **requirements.txt** - Dependencies
- **.env** - API keys (not committed)

---

## 🔐 Security

### ✅ Allowed
- SELECT queries
- JOINs
- GROUP BY
- Filtering (WHERE)
- Sorting (ORDER BY)

### ❌ Blocked
- INSERT (add data)
- UPDATE (modify data)
- DELETE (remove data)
- ALTER (change schema)

---

## 📊 Visualizations

**Auto-selects best chart:**
- Bar chart → Default for most queries
- Pie chart → When "pie" mentioned
- Line chart → When "line" mentioned

---

## 🛠️ Configuration

**OpenAI Settings** (openai.py)
`python
model = "gpt-4o"
temperature = 0
max_tokens = 2048
`

**RAG Settings** (rag_engine.py)
`python
chunk_size = 500
chunk_overlap = 50
`

**Security** (app.py)
`python
blocked_keywords = ["insert", "update", "delete", "drop", "create", "alter"]
`

---

## 📈 Performance

- Response time: 2-5 seconds
- Max query length: 500 chars
- Handles 10,000+ rows
- Instant chart rendering

---

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Invalid API Key | Check OpenAI credentials |
| DB connection failed | Verify Oracle host/port |
| "Unsafe code" error | Query blocked (INSERT/UPDATE/DELETE not allowed) |
| No results | Simplify question or check table names |

---

## 📚 References

- [Streamlit Docs](https://docs.streamlit.io/)
- [OpenAI API](https://platform.openai.com/docs/)
- [Oracle Python Client](https://python-oracledb.readthedocs.io/)
- [FAISS](https://github.com/facebookresearch/faiss)

---

## 👤 Author

**Kirti Upadhyay**
- Email: ukirti1911@gmail.com
- GitHub: [@kirtiu](https://github.com/kirtiu)

---

Translating curiosity into data: Built with Streamlit, OpenAI, Oracle Database, and FAISS
