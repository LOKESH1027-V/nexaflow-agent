# NexaFlow Agentic AI 🤖

NexaFlow Agentic AI is a command-line AI assistant built using **LangChain, LangGraph, Groq, FAISS, and Hugging Face embeddings**.

The agent can answer questions about NexaFlow's:

* 💰 Revenue
* 👥 Active customers
* 📉 Customer churn
* 📚 Company policies and definitions
* 💳 Pricing plans
* 📊 Customer success metrics

The agent uses **tools and a vector database** to retrieve company-specific information instead of relying only on the LLM's general knowledge.

---

## 🚀 Features

* 🤖 AI-powered company assistant
* 🧠 Tool-calling using LangChain
* 🔀 Agent workflow using LangGraph
* 💰 Revenue lookup by month
* 👥 Active customer information
* 📉 Churn information
* 📚 Knowledge-base retrieval
* 🔎 FAISS vector search
* 🧩 Hugging Face embeddings
* ⚡ Groq LLM
* 💻 Interactive command-line interface (CLI)

---

## 🏗️ Architecture

```text
                 User
                  │
                  ▼
            Command Line
               Interface
                  │
                  ▼
             LangGraph
                  │
                  ▼
              LLM Agent
                  │
          ┌───────┴────────┐
          │                │
          ▼                ▼
      Company Tools     Knowledge
          │             Retriever
          │                │
          │              FAISS
          │                │
          │       Hugging Face Embeddings
          │
          └────────┬────────┘
                   │
                   ▼
              Tool Result
                   │
                   ▼
                  LLM
                   │
                   ▼
             Final Answer
```

---

## 🛠️ Technologies Used

| Technology   | Purpose                               |
| ------------ | ------------------------------------- |
| Python       | Programming language                  |
| LangChain    | LLM and tool integration              |
| LangGraph    | Agent workflow                        |
| Groq         | LLM provider                          |
| FAISS        | Vector database                       |
| Hugging Face | Text embeddings                       |
| Pydantic     | Input validation                      |
| uv           | Python package/environment management |

---

## 📂 Project Structure

```text
nexaflow-agent/
│
├── agent.py              # Agent and LangGraph workflow
├── cli.py                # Command-line interface
├── .env                  # API keys (not committed)
├── .gitignore            # Ignored files
├── pyproject.toml        # Project dependencies
├── uv.lock               # Locked dependencies
└── README.md             # Project documentation
```

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd nexaflow-agent
```

### 2. Install dependencies

This project uses `uv`.

```bash
uv sync
```

If you don't have `uv`, install it first from the official documentation.

---

## 🔑 Environment Variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

Never commit your `.env` file to GitHub.

The `.gitignore` already contains:

```gitignore
.env
```

---

## ▶️ Running the Application

Start the CLI using:

```bash
uv run python cli.py
```

You should see something similar to:

```text
          NexaFlow Agetic AI

You can ask question about the related to the company policy,
income and active customers:
If you want to exit type 'exit'

Your question:
```

You can then ask questions such as:

```text
Your question: what is the income of january
```

```text
Your question: what is a high-value customer?
```

```text
Your question: what are the pricing plans?
```

```text
Your question: what is the healthy churn rate?
```

```text
Your question: how does NexaFlow track customer success?
```

To exit:

```text
Your question: exit

Thanks, see you
```

---

## 🧠 Example Knowledge

The NexaFlow knowledge base contains information such as:

### High-Value Customer

A high-value customer is a customer paying **over $2,000 per month** in subscription fees.

### Pricing

| Plan       | Monthly Cost |
| ---------- | -----------: |
| Starter    |         $500 |
| Growth     |       $1,500 |
| Enterprise |       $3,000 |

### Healthy Churn

NexaFlow considers a churn rate below **2% of active customers per month** healthy.

### Customer Success

Customer success is primarily tracked through **quarterly Net Promoter Score (NPS) surveys**.

---

## 🔧 Agent Tools

The agent uses multiple tools to access company information.

### `get_revenue`

Retrieves revenue for a specific month.

Example:

```text
What is the revenue in January?
```

### `get_customer_count`

Retrieves the number of active customers.

### `get_churn_count`

Retrieves the churn count for a specific month.

### `knowledge_lookup`

Searches the NexaFlow knowledge base using:

```text
Hugging Face Embeddings
        ↓
FAISS
        ↓
Relevant Documents
```

This allows the agent to answer questions about company policies, pricing, definitions, and customer success.

---

## 🔄 Agent Workflow

The LangGraph workflow follows this pattern:

```text
START
  │
  ▼
LLM
  │
  ▼
Does the LLM need a tool?
  │
  ├── No ─────────────► END
  │
  └── Yes
       │
       ▼
    ToolNode
       │
       ▼
      LLM
       │
       ▼
      END
```

`tools_condition` determines whether the LLM requested a tool.

`ToolNode` executes the requested tool.

The result is then sent back to the LLM so it can generate the final response.

---

## 🔐 Security

Do not commit API keys or secrets.

Make sure these files remain ignored:

```text
.env
.venv/
__pycache__/
*.pyc
```

---

## 📌 Future Improvements

Possible improvements for the project:

* [ ] Streaming responses in CLI
* [ ] Conversation history
* [ ] Better CLI formatting
* [ ] Add more company tools
* [ ] Add web interface
* [ ] Add FastAPI backend
* [ ] Add authentication
* [ ] Improve retrieval with metadata filtering
* [ ] Add evaluation/testing for agent responses
* [ ] Deploy the agent

---

## 👨‍💻 Author

**Lokesh**

Built as a learning project to explore:

* LangChain
* LangGraph
* RAG
* Vector databases
* Tool calling
* Agentic AI
* LLM applications
