# 🗄️ Oracle NL-SQL Chatbot

An intelligent chatbot that converts natural language questions into Oracle SQL queries, executes them safely, and visualizes results with automatic explanations. Powered by OpenAI GPT-4 and RAG (Retrieval-Augmented Generation).

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-Latest-red)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o-black)
![Oracle](https://img.shields.io/badge/Oracle-Database-red)
![License](https://img.shields.io/badge/License-MIT-green)

---

## ✨ Features

### 🎯 Core Functionality
- **💬 Natural Language to SQL** - Ask questions in plain English, get SQL queries executed
- **🔒 Safe Query Execution** - Blocks dangerous operations (INSERT, UPDATE, DELETE)
- **🤖 Intent Classification** - AI understands if it's a greeting, question, or database query
- **📊 Auto-Visualization** - Generates bar, pie, or line charts based on query results
- **🧠 RAG Engine** - Uses FAISS vector search for knowledge-aware SQL generation

### 🛡️ Security Features
- **Query Validation** - Detects and blocks modification queries
- **Whitelist Approach** - Only SELECT queries allowed
- **Error Handling** - Graceful error messages without exposing system details
- **Safe Execution** - Read-only database access

### 📈 Intelligence
- **Explanation Generation** - AI explains query results in business-friendly language
- **Dynamic SQL Generation** - Generates custom SQL for each question
- **Context Awareness** - Uses knowledge base for accurate query generation
- **Intelligent Chart Selection** - Auto-selects best visualization type

---

## 🏗️ Architecture

`
User Question (Natural Language)
    ↓
[Intent Classification] - Greeting? Question? SQL Query?
    ↓
[Query Generation] - LLM generates Oracle SQL with RAG context
    ↓
[Safety Validation] - Check for dangerous operations
    ↓
[Database Execution] - Run against Oracle DB
    ↓
[Result Visualization] - Auto-generate charts (bar/pie/line)
    ↓
[AI Explanation] - GPT explains findings
    ↓
User Gets Answer + Chart
`

### 🔧 Tech Stack
| Component | Technology |
|-----------|-----------|
| **Frontend** | Streamlit |
| **LLM** | OpenAI GPT-4o |
| **Database** | Oracle Database (oracledb) |
| **Vector Search** | FAISS |
| **Visualization** | Plotly |
| **Data Processing** | Pandas, NumPy |
| **Environment** | Python-dotenv |

---

## 📋 Prerequisites

- Python 3.8+
- Oracle Database (with read access)
- OpenAI API key (get from https://platform.openai.com/)
- pip (Python package manager)

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
`ash
git clone https://github.com/kirtiu/oracle-nl-sql-chatbot.git
cd oracle-nl-sql-chatbot
`

### 2. Create Virtual Environment
`ash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
`

### 3. Install Dependencies
`ash
pip install -r requirements.txt
`

### 4. Set Up Environment Variables
Create a .env file in the root directory:
`env
# Required: OpenAI API Configuration
OPENAI_API_KEY=sk-your-api-key-here

# Required: Oracle Database Configuration
ORACLE_USER=your_oracle_username
ORACLE_PASSWORD=your_oracle_password
ORACLE_HOST=your_oracle_host
ORACLE_PORT=1521
ORACLE_SID=your_oracle_sid

# Optional: Model Configuration
OPENAI_MODEL=gpt-4o
OPENAI_TEMPERATURE=0
`

### 5. Run the Application
`ash
streamlit run app.py
`

The app will open at: **http://localhost:8501**

---

## 🎯 Usage

### Quick Start
1. **Launch the app** - Run streamlit run app.py
2. **Ask a question** - "How many Employees are there in Sales Department?"
3. **View results** - See SQL, data table, and chart automatically
4. **Read explanation** - AI explains what the data means

### Chat Examples

`
User: "How many employees are in each department?"
Bot: [Generates SQL] → [Shows table] → [Creates bar chart] → [Explains findings]

User: "Show me salary distribution by job role"
Bot: [SQL with GROUP BY] → [Data table] → [Pie chart] → [Interpretation]

User: "Compare average salaries across departments"
Bot: [Aggregation query] → [Results] → [Line chart] → [Summary]

User: "hello"
Bot: "👋 Hi there! Nice to hear from you. Please ask a valid database-related question."

User: "What is SQL?"
Bot: "Please enter a valid database-related question."
`

### Question Types

✅ **Valid Questions:**
`
"How many employees are in the Sales department?"
"Show me the top 5 highest-paid employees"
"What is the average salary by department?"
"List all products with sales over "
"Show me the distribution of employees by location"
`

❌ **Blocked Operations:**
`
"DELETE all employees" → Blocked (modification)
"INSERT new employee" → Blocked (modification)
"UPDATE salary values" → Blocked (modification)
"CREATE new table" → Blocked (modification)
`

---

## 📊 Project Structure

`
oracle-nl-sql-chatbot/
├── app.py                         # Main Streamlit application
├── db.py                          # Oracle database connection & queries
├── openai.py                      # OpenAI integration & intent classification
├── rag_engine.py                  # FAISS RAG implementation
├── visualizer.py                  # Chart generation with Plotly
├── oracle_chatbot_knowledge.txt   # Knowledge base for RAG
├── requirements.txt               # Python dependencies
├── .env                           # Environment variables (not committed)
├── chatbot_debug.log              # Debug log (auto-created)
└── README.md                      # This file
`

---

## 🔐 Security & Safety

### Why Safety Checks?
Unvalidated SQL generation can accidentally:
- Modify or delete important data
- Access unauthorized tables
- Consume excessive resources
- Expose sensitive information

### What's Blocked?
`
❌ INSERT queries       # Cannot add data
❌ UPDATE queries       # Cannot modify data
❌ DELETE queries       # Cannot remove data
❌ CREATE/DROP          # Cannot change schema
❌ ALTER commands       # Cannot alter tables
`

### What's Allowed?
`
✅ SELECT queries       # Read data
✅ JOIN operations     # Combine tables
✅ Aggregation         # GROUP BY, SUM, AVG, COUNT
✅ Filtering           # WHERE conditions
✅ Sorting             # ORDER BY
`

---

## 📈 Performance

- **Response Time**: 2-5 seconds (includes LLM + SQL execution)
- **Max Query Length**: 500 characters
- **Max Result Rows**: Handles 10,000+ rows efficiently
- **Concurrent Users**: Single-session Streamlit app
- **Chart Rendering**: Instant with Plotly

---

## 🐛 Troubleshooting

### "Invalid API Key" Error
- Verify your OpenAI API key is correct
- Check it has access to GPT-4o
- Ensure .env file is in project root

### "Cannot connect to Oracle Database"
- Verify Oracle credentials in .env
- Check ORACLE_HOST and ORACLE_PORT
- Ensure database is accessible from your network

### "Unsafe code detected"
- User asked for INSERT/UPDATE/DELETE query
- These operations are intentionally blocked for safety

### "No results found"
- Generated SQL might not match your schema
- Try simpler questions
- Check knowledge base has correct table/column names

---

## 📚 References

- [Streamlit Documentation](https://docs.streamlit.io/)
- [OpenAI API Docs](https://platform.openai.com/docs/)
- [Oracle Database Python Client](https://python-oracledb.readthedocs.io/)
- [FAISS Vector Search](https://github.com/facebookresearch/faiss)
- [Plotly Visualization](https://plotly.com/python/)

---

## 📄 License

This project is licensed under the MIT License.

---

## 👤 Author

**Kirti Upadhyay**
- Email: ukirti1911@gmail.com
- GitHub: [@kirtiu](https://github.com/kirtiu)

---

## ⭐ Show Your Support

If you found this project helpful, please give it a ⭐ on GitHub!

---

Translating curiosity into data: Built with Streamlit, OpenAI, Oracle Database, and FAISS
