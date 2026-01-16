<h1 align="center">🚀 CrewAI Multi-Agent Projects Collection</h1>

<p align="center">
  <strong>A comprehensive showcase of AI agents collaborating to solve complex real-world problems</strong>
</p>

<p align="center">
  <a href="#-projects">Projects</a> •
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-contributing">Contributing</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/CrewAI-Latest-purple?style=for-the-badge" alt="CrewAI"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License"/>
  <img src="https://img.shields.io/badge/AI%20Agents-Multi--Agent-orange?style=for-the-badge" alt="AI Agents"/>
</p>

---

## 🌟 Overview

Welcome to the **CrewAI Multi-Agent Projects Collection** — a curated repository of intelligent AI agent systems built using the powerful [CrewAI](https://www.crewai.com/) framework. This collection demonstrates how autonomous AI agents can collaborate, debate, analyze, and create solutions across diverse domains.

**What's Inside:**
- 🤖 **5 Complete Projects** ready to run
- 🧠 **Multiple LLM Support** (OpenAI GPT-4o, Claude 3.7 Sonnet)
- 🔧 **Custom Tools** (Push notifications, Web search)
- 💾 **Advanced Memory Systems** (Long-term, Short-term, Entity)
- 📊 **Structured Outputs** with Pydantic models

---

## 📂 Projects

### 💻 Coder
> **AI-Powered Python Developer with Safe Code Execution**

A single-agent crew that writes, executes, and validates Python code in a secure Docker environment. Perfect for automated coding tasks and mathematical computations.

| Component | Details |
|-----------|---------|
| **Agents** | 1 — Python Developer |
| **Tasks** | 1 — coding_task |
| **LLM** | `gpt-4o-mini` |
| **Process** | Sequential |

**Key Features:**
- ✅ Docker-based safe code execution
- ✅ Automatic code planning and validation
- ✅ Output includes both code and execution results

**Example Use Case:**
```python
assignment = 'Write a python program to calculate the first 10,000 terms \
    of this series, multiplying the total by 4: 1 - 1/3 + 1/5 - 1/7 + ...'
```

```bash
cd coder
crewai run
# Output: output/code_and_output.txt
```

---

### ⚔️ Debate
> **AI Agents Engaging in Structured Debates**

A debate simulation where one agent argues both sides of a motion, and a separate judge agent decides the winner based purely on argument merit.

| Component | Details |
|-----------|---------|
| **Agents** | 2 — Debater, Judge |
| **Tasks** | 3 — propose, oppose, decide |
| **LLMs** | `gpt-4o-mini` (Debater), `claude-3-7-sonnet` (Judge) |
| **Process** | Sequential |

**Workflow:**
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   PROPOSE   │ ──▶ │   OPPOSE    │ ──▶ │   DECIDE    │
│  (Debater)  │     │  (Debater)  │     │   (Judge)   │
│  GPT-4o-mini│     │  GPT-4o-mini│     │Claude Sonnet│
└─────────────┘     └─────────────┘     └─────────────┘
```

**Example Motion:**
```python
inputs = {
    'motion': 'There needs to be strict laws to regulate LLMs',
}
```

```bash
cd debate
crewai run
# Outputs: output/propose.md, output/oppose.md, output/decide.md
```

---

### 🔧 Engineering Team
> **Full Software Development Team Simulation**

A complete engineering team that takes requirements and delivers working code with tests and a UI. Simulates the collaboration between lead, backend, frontend, and QA engineers.

| Component | Details |
|-----------|---------|
| **Agents** | 4 — Engineering Lead, Backend Engineer, Frontend Engineer, Test Engineer |
| **Tasks** | 4 — design_task, code_task, frontend_task, test_task |
| **LLMs** | `gpt-4o` (Lead), `claude-3-7-sonnet` (Engineers) |
| **Process** | Sequential with task dependencies |

**Agent Roles:**

| Agent | Role | LLM | Special Capabilities |
|-------|------|-----|---------------------|
| 🏗️ **Engineering Lead** | Creates detailed designs from requirements | GPT-4o | — |
| ⚙️ **Backend Engineer** | Implements the design in Python | Claude 3.7 Sonnet | Code Execution |
| 🎨 **Frontend Engineer** | Builds Gradio UI for the backend | Claude 3.7 Sonnet | — |
| 🧪 **Test Engineer** | Writes comprehensive unit tests | Claude 3.7 Sonnet | Code Execution |

**Example Requirements:**
```python
requirements = """
A simple account management system for a trading simulation platform.
- Create accounts, deposit/withdraw funds
- Buy/sell shares with quantity tracking
- Calculate portfolio value and profit/loss
- Prevent invalid transactions
"""
```

```bash
cd engineering_team
crewai run
# Outputs: 
#   output/accounts.py_design.md
#   output/accounts.py
#   output/app.py (Gradio UI)
#   output/test_accounts.py
```

---

### 📊 Financial Researcher
> **AI-Powered Company Analysis and Reporting**

A research crew that investigates companies and produces comprehensive financial reports with market analysis.

| Component | Details |
|-----------|---------|
| **Agents** | 2 — Researcher, Analyst |
| **Tasks** | 2 — research_task, analysis_task |
| **LLM** | `gpt-4o-mini` |
| **Tools** | `SerperDevTool` (Web Search) |
| **Process** | Sequential with context passing |

**Workflow:**
```
┌──────────────────┐         ┌──────────────────┐
│    RESEARCHER    │  ────▶  │     ANALYST      │
│  Gathers data    │ context │  Writes report   │
│  SerperDevTool   │         │                  │
└──────────────────┘         └──────────────────┘
```

**Report Sections:**
- Executive Summary
- Company Status & Health
- Historical Performance
- Challenges & Opportunities
- Market Outlook

```bash
cd financial_researcher
crewai run
# Output: output/report.md
```

---

### 📈 Stock Picker
> **Intelligent Stock Selection with Memory & Notifications**

The most advanced crew in the collection — uses hierarchical management, persistent memory, and push notifications to find and recommend trending stocks.

| Component | Details |
|-----------|---------|
| **Agents** | 4 — Manager, Trending Company Finder, Financial Researcher, Stock Picker |
| **Tasks** | 3 — find_trending_companies, research_trending_companies, pick_best_company |
| **LLMs** | `gpt-4o` (Manager), `gpt-4o-mini` (Workers) |
| **Tools** | `SerperDevTool`, **Custom `PushNotificationTool`** |
| **Process** | **Hierarchical** (Manager delegates) |

**Advanced Features:**

| Feature | Implementation |
|---------|----------------|
| 🧠 **Long-Term Memory** | SQLite storage for persistent learning |
| 💭 **Short-Term Memory** | RAG storage with OpenAI embeddings |
| 🏷️ **Entity Memory** | Tracks key information about companies |
| 📱 **Push Notifications** | Pushover API integration |
| 📊 **Structured Output** | Pydantic models for type-safe data |

**Architecture:**
```
                    ┌─────────────────┐
                    │     MANAGER     │
                    │     (GPT-4o)    │
                    │  Orchestrates   │
                    └────────┬────────┘
                             │ delegates
        ┌────────────────────┼────────────────────┐
        ▼                    ▼                    ▼
┌───────────────┐   ┌───────────────┐   ┌───────────────┐
│   FINDER      │   │  RESEARCHER   │   │ STOCK PICKER  │
│ Find trending │──▶│ Deep analysis │──▶│ Final pick    │
│ SerperDevTool │   │ SerperDevTool │   │ PushNotify    │
└───────────────┘   └───────────────┘   └───────────────┘
```

**Custom Push Notification Tool:**
```python
# Sends real-time alerts via Pushover
class PushNotificationTool(BaseTool):
    name: str = "Send a Push Notification"
    # Integrates with Pushover API for instant alerts
```

```bash
cd stock_picker
crewai run
# Outputs:
#   output/trending_companies.json
#   output/research_report.json  
#   output/decision.md
#   + Push notification to your device!
```

---

## 🏗️ Architecture

### Project Structure
```
crewai/
├── coder/
│   ├── output/                    # Generated code and results
│   ├── knowledge/                 # Knowledge base files
│   └── src/coder/
│       ├── config/
│       │   ├── agents.yaml        # Agent definitions
│       │   └── tasks.yaml         # Task configurations
│       ├── tools/                 # Custom tools
│       ├── crew.py                # Crew orchestration
│       └── main.py                # Entry point
│
├── debate/
│   ├── output/                    # Debate arguments and decision
│   └── src/debate/
│       └── ...
│
├── engineering_team/
│   ├── output/                    # Design, code, UI, tests
│   ├── example_output_*/          # Sample outputs
│   └── src/engineering_team/
│       └── ...
│
├── financial_researcher/
│   ├── output/                    # Research reports
│   └── src/financial_researcher/
│       └── ...
│
└── stock_picker/
    ├── output/                    # Stock analysis results
    ├── memory/                    # Persistent memory storage
    └── src/stock_picker/
        ├── tools/
        │   └── push_tool.py       # Custom Pushover integration
        └── ...
```

### CrewAI Components

```
┌─────────────────────────────────────────────────────────────────┐
│                        CrewAI Framework                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│   ┌─────────┐    ┌─────────┐    ┌─────────┐                     │
│   │ Agent 1 │───▶│ Agent 2 │───▶│ Agent N │                     │
│   │  Role   │    │  Role   │    │  Role   │                     │
│   │  Goal   │    │  Goal   │    │  Goal   │                     │
│   │  LLM    │    │  LLM    │    │  LLM    │                     │
│   │  Tools  │    │  Tools  │    │  Tools  │                     │
│   └────┬────┘    └────┬────┘    └────┬────┘                     │
│        │              │              │                           │
│        ▼              ▼              ▼                           │
│   ┌─────────┐    ┌─────────┐    ┌─────────┐                     │
│   │ Task 1  │───▶│ Task 2  │───▶│ Task N  │                     │
│   │ context │    │ context │    │ output  │                     │
│   └─────────┘    └─────────┘    └─────────┘                     │
│                                                                  │
│                    ┌───────────────────┐                        │
│                    │       Crew        │                        │
│                    │  Sequential /     │                        │
│                    │  Hierarchical     │                        │
│                    └───────────────────┘                        │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📁 Example Outputs

Each project includes example outputs so you can see what the crews produce before running them yourself.

| Project | Output Location | Files |
|---------|-----------------|-------|
| **coder** | `coder/output/` | `code_and_output.txt` |
| **debate** | `debate/output/` | `propose.md`, `oppose.md`, `decide.md` |
| **engineering_team** | `engineering_team/example_output_*/` | Design docs, Python modules, Gradio UI, Unit tests |
| **financial_researcher** | `financial_researcher/output/` | `report.md` |
| **stock_picker** | `stock_picker/output/` | `trending_companies.json`, `research_report.json`, `decision.md` |

> 💡 **Tip:** The `engineering_team` project has multiple example outputs (`example_output_4o`, `example_output_mini`, `example_output_new`) showing results from different LLM configurations.

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10 - 3.13
- Docker Desktop (for code execution in `coder` and `engineering_team`)
- API Keys (see Configuration)

### Installation

```bash
# Clone the repository
git clone https://github.com/Itsme-aniketghosh/crewai.git
cd crewai

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install CrewAI with tools
pip install crewai crewai-tools

# Install additional dependencies
pip install gradio requests pydantic
```

### Running Projects

```bash
# Run any project
cd <project_name>
crewai run

# Or directly with Python
python -m <project_name>.main
```

---

## ⚙️ Configuration

### Environment Variables

Create a `.env` file in each project directory:

```env
# Required for all projects
OPENAI_API_KEY=your-openai-key

# Required for projects using Claude (debate, engineering_team)
ANTHROPIC_API_KEY=your-anthropic-key

# Required for web search (financial_researcher, stock_picker)
SERPER_API_KEY=your-serper-key

# Required for push notifications (stock_picker)
PUSHOVER_USER=your-pushover-user
PUSHOVER_TOKEN=your-pushover-token
```

### LLM Configuration by Project

| Project | LLMs Used |
|---------|-----------|
| **coder** | `gpt-4o-mini` |
| **debate** | `gpt-4o-mini`, `claude-3-7-sonnet-latest` |
| **engineering_team** | `gpt-4o`, `claude-3-7-sonnet-latest` |
| **financial_researcher** | `gpt-4o-mini` |
| **stock_picker** | `gpt-4o`, `gpt-4o-mini` |

---

## 🛠️ Tools & Technologies

### Built-in Tools

| Tool | Description | Used In |
|------|-------------|---------|
| `SerperDevTool` | Google search via Serper API | financial_researcher, stock_picker |

### Custom Tools

| Tool | Description | Used In |
|------|-------------|---------|
| `PushNotificationTool` | Send alerts via Pushover API | stock_picker |

### Special Features

| Feature | Description | Used In |
|---------|-------------|---------|
| **Code Execution** | Safe Docker-based Python execution | coder, engineering_team |
| **Memory System** | LTM (SQLite) + STM (RAG) + Entity | stock_picker |
| **Hierarchical Process** | Manager agent delegates tasks | stock_picker |
| **Pydantic Output** | Type-safe structured responses | stock_picker |
| **Task Context** | Pass output between tasks | engineering_team, financial_researcher, stock_picker |

---

## 📚 Learning Path

**Recommended order to explore the projects:**

1. **🟢 coder** — Simplest, single agent with code execution
2. **🟢 debate** — Two agents, multi-task workflow
3. **🟡 financial_researcher** — Web search tools, task context
4. **🟡 engineering_team** — Multi-agent collaboration, multiple LLMs
5. **🔴 stock_picker** — Advanced: hierarchical process, memory, custom tools

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Ideas for Contribution

- 🆕 New crew projects (marketing, customer service, content creation)
- 🔧 Additional custom tools
- 📝 Documentation improvements
- 🧪 Example outputs and test cases

---

## 📚 Resources

- [CrewAI Documentation](https://docs.crewai.com/)
- [CrewAI GitHub](https://github.com/crewAIInc/crewAI)
- [CrewAI Examples](https://github.com/crewAIInc/crewAI-examples)
- [Learn CrewAI](https://learn.crewai.com/)
- [Serper API](https://serper.dev/)
- [Pushover API](https://pushover.net/)

---

## 👨‍💻 Author

**Aniket Ghosh**

- GitHub: [@Itsme-aniketghosh](https://github.com/Itsme-aniketghosh)

---

<p align="center">
  Made with ❤️ and 🤖 AI Agents
</p>