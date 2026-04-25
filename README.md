# GenAI Observability with MLflow and Arize Phoenix

![learnwithparam.com](https://www.learnwithparam.com/ai-bootcamp/opengraph-image)

Instrument a real multi-tool agent with MLflow tracking and Arize Phoenix tracing. A LangGraph router picks between SQL, RAG, and web search tools, and every decision, prompt, and tool call shows up in a dashboard you can click through.

> Start learning at [learnwithparam.com](https://learnwithparam.com). Regional pricing available with discounts of up to 60%.

## What You'll Learn

- Instrument an LLM app with MLflow auto-logging and custom spans
- Trace every prompt and tool call with Arize Phoenix via OpenInference
- Build a LangGraph router that dispatches between SQL, RAG, and web search tools
- Log the SQL query, the RAG chunks, and the web results that led to each answer
- Debug hallucinations and routing errors by replaying traces in the Phoenix UI
- Set up MLflow experiments so you can compare prompt variants across runs

## Tech Stack

- **Python 3.11+** with `uv` for dependency management
- **LangGraph** for the router agent state graph
- **OpenAI** for the chat LLM
- **FAISS** + **sentence-transformers** for local RAG
- **SQLite** for the e-commerce data warehouse
- **Serper** for live web search
- **MLflow** for experiment tracking
- **Arize Phoenix** + OpenInference for OpenTelemetry-style LLM tracing

## Getting Started

### Prerequisites

- Python 3.11+
- [uv](https://docs.astral.sh/uv/) (installed automatically by `make setup`)
- An OpenAI API key
- A Serper API key (free tier works)

### Quick Start

```bash
make dev

# Or step by step:
make setup           # install deps, create .env
# Edit .env with OPENAI_API_KEY and SERPER_API_KEY
make setup-data      # downloads dataset and builds FAISS + SQLite indexes
make run             # interactive agent
make demo            # scripted multi-turn demo
```

Open the Phoenix UI at [http://localhost:6006](http://localhost:6006) and the MLflow UI at [http://localhost:5000](http://localhost:5000) to inspect traces and runs.

### With Docker

```bash
make build
make up
make logs
make down
```

## Challenges

Work through these incrementally:

1. **Instrument OpenAI** - Wire OpenInference to trace every OpenAI call into Phoenix
2. **Log Prompts to MLflow** - Start an MLflow run and log the prompt, params, and response
3. **Custom Spans** - Create spans for `retrieve`, `sql_query`, and `web_search` tool calls
4. **Router Node** - Build a LangGraph router that picks `sql`, `rag`, or `web_search`
5. **SQL Tool** - Query the SQLite warehouse with a safety-checked SQL generator
6. **RAG Tool** - Retrieve from FAISS with a configurable top-k
7. **Web Search Tool** - Use Serper, log the query and top results as a span attribute
8. **Trace-Driven Debugging** - Replay a failing trace in Phoenix and fix the routing rule

## Makefile Targets

```
make help           Show all available commands
make setup          Initial setup (create .env, install deps)
make setup-data     Download the dataset and build FAISS + SQLite indexes
make dev            Setup, load data, run
make run            Run the interactive agent
make demo           Run the scripted demo
make build          Build Docker image
make up             Start container (exposes Phoenix :6006 and MLflow :5000)
make down           Stop container
make clean          Remove venv and caches
```

## Learn more

- Start the course: [learnwithparam.com/courses/llm-observability-mlflow](https://www.learnwithparam.com/courses/llm-observability-mlflow)
- AI Bootcamp for Software Engineers: [learnwithparam.com/ai-bootcamp](https://www.learnwithparam.com/ai-bootcamp)
- All courses: [learnwithparam.com/courses](https://www.learnwithparam.com/courses)
