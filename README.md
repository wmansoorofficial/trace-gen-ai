# TraceGenAI – AI Agent for Analyzing Production Logs and Performing RCA

## Architecture
<img width="2048" height="2080" alt="Gemini_Generated_Image_lggbrulggbrulggb" src="https://github.com/user-attachments/assets/9fab509d-4255-42a4-9a6e-e5d85860a1d3" />



## Tech Stack Used

- LangChain
- Python 3.12
- Tavily API
- SQLite
- OpenAI – gpt-5-nano
- LangSmith
- InMemoryVectorStore (for RAG)
- uv

---

## Description

TraceGenAI is a multi-agent system designed to analyze production logs and perform Root Cause Analysis (RCA).

The system uses a Coordinator Agent that receives raw log input. The log is then processed by a series of specialized agents, each responsible for a specific task in the analysis pipeline.

### Workflow

1. The Coordinator Agent receives the raw production log.
2. The log is passed to the Log Parser Agent, which converts it into a properly structured JSON format.
3. The structured log is sent to the Web Search Agent, which searches the internet using the Tavily API to gather relevant external information.
4. The log is forwarded to the Logs DB Agent, which checks its frequency and occurrence statistics in a SQLite database.
5. The log is then passed to the Incident Search Agent, which uses a RAG (Retrieval-Augmented Generation) approach to find semantically similar past incidents from stored documents.
6. All collected data is sent to the RCA Agent, which analyzes the aggregated information, determines the most probable root cause, and generates a step-by-step resolution plan.
7. The resolution steps are returned to the Coordinator Agent, which compiles and sends the final response to the user.

---

## Agents / Sub-Agent Details

| Agent Function            | Agent Name              |
|---------------------------|-------------------------|
| Coordinator Agent         | coordinator             |
| Logs Parser Agent         | log_parser_agent        |
| Web Search Agent          | web_search_agent        |
| Logs Statistics Agent     | logs_db_agent           |
| Incident Search Agent     | incident_search_agent   |
| Root Cause Analysis Agent | rca_agent               |

## Langsmith Trace
https://smith.langchain.com/public/a113b7dd-609d-4df1-9ecc-0447660a2531/r
