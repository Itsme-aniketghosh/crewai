# 💻 Coder

> AI-Powered Python Developer with Safe Code Execution

A single-agent CrewAI project that writes, executes, and validates Python code in a secure Docker environment.

## 🎯 Overview

This crew features a Python Developer agent that:
1. Plans how the code will work
2. Writes clean, efficient Python code
3. Executes it safely in Docker
4. Returns both the code and its output

## 🤖 Agent

| Agent | Role | LLM |
|-------|------|-----|
| **Coder** | Python Developer | `gpt-4o-mini` |

**Capabilities:**
- ✅ Code execution enabled
- ✅ Safe mode (Docker containerized)
- ✅ 30-second execution timeout
- ✅ 3 retry attempts on failure

## 📋 Task

| Task | Description | Output |
|------|-------------|--------|
| **coding_task** | Write Python code to achieve the assignment | `output/code_and_output.txt` |

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- Docker Desktop ([Install here](https://docs.docker.com/desktop/))
- OpenAI API key

### Installation

```bash
cd coder
pip install crewai crewai-tools
```

### Configuration

Create a `.env` file:
```env
OPENAI_API_KEY=your-openai-key
```

### Run

```bash
crewai run
```

Or modify the assignment in `main.py`:
```python
assignment = 'Write a python program to calculate the first 10,000 terms \
    of this series, multiplying the total by 4: 1 - 1/3 + 1/5 - 1/7 + ...'
```

## 📁 Output

Results are saved to `output/code_and_output.txt` containing:
- The generated Python code
- The execution output/results

## 📂 Project Structure

```
coder/
├── output/
│   └── code_and_output.txt
├── knowledge/
└── src/coder/
    ├── config/
    │   ├── agents.yaml
    │   └── tasks.yaml
    ├── tools/
    │   └── custom_tool.py
    ├── crew.py
    └── main.py
```

## 💡 Example Use Cases

- Mathematical computations and series calculations
- Data processing scripts
- Algorithm implementations
- Code generation from natural language descriptions

## ⚠️ Notes

- Requires Docker Desktop for safe code execution
- Execution timeout is set to 30 seconds
- The agent will retry up to 3 times on failure