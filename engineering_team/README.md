# 🔧 Engineering Team

> Full Software Development Team Simulation

A complete engineering team that takes requirements and delivers working code with tests and a UI. Simulates the collaboration between lead, backend, frontend, and QA engineers.

## 🎯 Overview

This crew simulates a full software development workflow:
1. **Engineering Lead** creates detailed design from requirements
2. **Backend Engineer** implements the Python module
3. **Frontend Engineer** builds a Gradio UI
4. **Test Engineer** writes comprehensive unit tests

## 🤖 Agents

| Agent | Role | LLM | Code Execution |
|-------|------|-----|----------------|
| 🏗️ **Engineering Lead** | Creates detailed designs | `gpt-4o` | ❌ |
| ⚙️ **Backend Engineer** | Implements Python code | `claude-3-7-sonnet` | ✅ |
| 🎨 **Frontend Engineer** | Builds Gradio UI | `claude-3-7-sonnet` | ❌ |
| 🧪 **Test Engineer** | Writes unit tests | `claude-3-7-sonnet` | ✅ |

## 📋 Tasks

| Task | Description | Agent | Output |
|------|-------------|-------|--------|
| **design_task** | Create detailed module design | Engineering Lead | `output/{module_name}_design.md` |
| **code_task** | Implement the Python module | Backend Engineer | `output/{module_name}` |
| **frontend_task** | Build Gradio demo UI | Frontend Engineer | `output/app.py` |
| **test_task** | Write unit tests | Test Engineer | `output/test_{module_name}` |

## 🔄 Workflow

```
┌──────────────────┐
│  ENGINEERING     │
│     LEAD         │
│    (GPT-4o)      │
│  Creates Design  │
└────────┬─────────┘
         │ design
         ▼
┌──────────────────┐
│    BACKEND       │
│   ENGINEER       │
│ (Claude Sonnet)  │
│ Writes Code      │
└────────┬─────────┘
         │ code
    ┌────┴────┐
    ▼         ▼
┌────────┐ ┌────────┐
│FRONTEND│ │  TEST  │
│  ENG   │ │  ENG   │
│Gradio  │ │ Tests  │
└────────┘ └────────┘
```

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- Docker Desktop (for code execution)
- OpenAI API key
- Anthropic API key

### Installation

```bash
cd engineering_team
pip install crewai crewai-tools gradio
```

### Configuration

Create a `.env` file:
```env
OPENAI_API_KEY=your-openai-key
ANTHROPIC_API_KEY=your-anthropic-key
```

### Run

```bash
crewai run
```

Or modify the requirements in `main.py`:
```python
requirements = """
A simple account management system for a trading simulation platform.
- Create accounts, deposit/withdraw funds
- Buy/sell shares with quantity tracking
- Calculate portfolio value and profit/loss
- Prevent invalid transactions
"""
module_name = "accounts.py"
class_name = "Account"
```

## 📁 Output

Four files are generated:
- `output/{module_name}_design.md` - Detailed design document
- `output/{module_name}` - The Python module
- `output/app.py` - Gradio UI for the module
- `output/test_{module_name}` - Unit tests

## 📂 Project Structure

```
engineering_team/
├── output/
├── example_output_4o/       # Sample output using GPT-4o
├── example_output_mini/     # Sample output using GPT-4o-mini
├── example_output_new/      # Latest sample output
├── knowledge/
└── src/engineering_team/
    ├── config/
    │   ├── agents.yaml
    │   └── tasks.yaml
    ├── tools/
    │   └── custom_tool.py
    ├── crew.py
    └── main.py
```

## 💡 Example Use Cases

- Rapid prototyping of Python applications
- Auto-generating trading/finance modules
- Creating CRUD applications with UI
- Building testable Python packages

## 🎨 Key Features

- **Multi-LLM Collaboration**: GPT-4o for design, Claude for implementation
- **Complete Deliverables**: Design, code, UI, and tests
- **Safe Code Execution**: Docker-containerized execution
- **Task Dependencies**: Each task builds on the previous
- **Production-Ready Output**: Clean, executable Python code