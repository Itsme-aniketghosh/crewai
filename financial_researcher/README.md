# 📊 Financial Researcher

> AI-Powered Company Analysis and Reporting

A research crew that investigates companies and produces comprehensive financial reports with market analysis.

## 🎯 Overview

This crew performs thorough company research:
1. **Researcher** gathers data from the web using search tools
2. **Analyst** synthesizes findings into a polished report

## 🤖 Agents

| Agent | Role | LLM | Tools |
|-------|------|-----|-------|
| 🔬 **Researcher** | Gathers financial data | `gpt-4o-mini` | `SerperDevTool` |
| 📝 **Analyst** | Writes comprehensive reports | `gpt-4o-mini` | — |

## 📋 Tasks

| Task | Description | Agent | Output |
|------|-------------|-------|--------|
| **research_task** | Conduct thorough company research | Researcher | (passed to analyst) |
| **analysis_task** | Create comprehensive report | Analyst | `output/report.md` |

## 🔄 Workflow

```
┌──────────────────┐         ┌──────────────────┐
│    RESEARCHER    │  ────▶  │     ANALYST      │
│  Gathers data    │ context │  Writes report   │
│  SerperDevTool   │         │                  │
│   GPT-4o-mini    │         │   GPT-4o-mini    │
└──────────────────┘         └──────────────────┘
```

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- OpenAI API key
- Serper API key ([Get one here](https://serper.dev/))

### Installation

```bash
cd financial_researcher
pip install crewai crewai-tools
```

### Configuration

Create a `.env` file:
```env
OPENAI_API_KEY=your-openai-key
SERPER_API_KEY=your-serper-key
```

### Run

```bash
crewai run
```

Or modify the company in `main.py`:
```python
inputs = {
    'company': 'Apple'
}
```

## 📁 Output

A comprehensive markdown report is saved to `output/report.md` containing:

1. **Executive Summary**
2. **Company Status & Health**
3. **Historical Performance**
4. **Challenges & Opportunities**
5. **Recent News & Events**
6. **Market Outlook**

## 📂 Project Structure

```
financial_researcher/
├── output/
│   └── report.md
├── knowledge/
└── src/financial_researcher/
    ├── config/
    │   ├── agents.yaml
    │   └── tasks.yaml
    ├── tools/
    │   └── custom_tool.py
    ├── crew.py
    └── main.py
```

## 💡 Example Companies to Research

- Apple
- Tesla
- NVIDIA
- Microsoft
- Amazon

## 🎨 Key Features

- **Web Search Integration**: Real-time data gathering via Serper
- **Task Context Passing**: Research flows seamlessly to analysis
- **Professional Reports**: Well-structured markdown output
- **Market Disclaimer**: Notes that reports shouldn't be used for trading decisions

## ⚠️ Disclaimer

The reports generated are for informational purposes only and should not be used as the sole basis for investment decisions. Always consult with a qualified financial advisor.