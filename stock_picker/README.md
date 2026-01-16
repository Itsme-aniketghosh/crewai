# 📈 Stock Picker

> Intelligent Stock Selection with Memory & Push Notifications

The most advanced crew in the collection — uses hierarchical management, persistent memory, and push notifications to find and recommend trending stocks.

## 🎯 Overview

This crew uses a sophisticated multi-agent hierarchy:
1. **Manager** orchestrates the entire workflow
2. **Trending Company Finder** discovers hot stocks in the news
3. **Financial Researcher** conducts deep analysis
4. **Stock Picker** makes final recommendations with push notifications

## 🤖 Agents

| Agent | Role | LLM | Tools | Memory |
|-------|------|-----|-------|--------|
| 👔 **Manager** | Orchestrates workflow | `gpt-4o` | — | — |
| 🔍 **Trending Company Finder** | Finds trending stocks | `gpt-4o-mini` | `SerperDevTool` | ✅ |
| 🔬 **Financial Researcher** | Deep company analysis | `gpt-4o-mini` | `SerperDevTool` | — |
| 📊 **Stock Picker** | Final recommendation | `gpt-4o-mini` | `PushNotificationTool` | ✅ |

## 📋 Tasks

| Task | Description | Agent | Output |
|------|-------------|-------|--------|
| **find_trending_companies** | Find 2-3 trending companies | Finder | `output/trending_companies.json` |
| **research_trending_companies** | Detailed analysis of each | Researcher | `output/research_report.json` |
| **pick_best_company** | Select best investment | Stock Picker | `output/decision.md` |

## 🏗️ Architecture

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
│    FINDER     │   │  RESEARCHER   │   │ STOCK PICKER  │
│Find trending  │──▶│Deep analysis  │──▶│ Final pick    │
│SerperDevTool  │   │SerperDevTool  │   │ PushNotify    │
│  GPT-4o-mini  │   │  GPT-4o-mini  │   │  GPT-4o-mini  │
└───────────────┘   └───────────────┘   └───────────────┘
```

## 🧠 Memory System

This project features a comprehensive memory system:

| Memory Type | Storage | Purpose |
|-------------|---------|---------|
| **Long-Term** | SQLite | Persistent storage across sessions |
| **Short-Term** | RAG (OpenAI embeddings) | Current context awareness |
| **Entity** | RAG (OpenAI embeddings) | Track key company information |

Memory is stored in the `memory/` folder and persists between runs.

## 📱 Custom Push Notification Tool

The `PushNotificationTool` sends real-time alerts via [Pushover](https://pushover.net/):

```python
class PushNotificationTool(BaseTool):
    name: str = "Send a Push Notification"
    # Sends instant alerts to your phone/device
```

## 📊 Structured Output

Uses Pydantic models for type-safe structured data:

- `TrendingCompany` - Company name, ticker, trending reason
- `TrendingCompanyList` - List of trending companies
- `TrendingCompanyResearch` - Detailed research on each company
- `TrendingCompanyResearchList` - All research compiled

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- OpenAI API key
- Serper API key
- Pushover account (for notifications)

### Installation

```bash
cd stock_picker
pip install crewai crewai-tools requests
```

### Configuration

Create a `.env` file:
```env
OPENAI_API_KEY=your-openai-key
SERPER_API_KEY=your-serper-key
PUSHOVER_USER=your-pushover-user
PUSHOVER_TOKEN=your-pushover-token
```

### Run

```bash
crewai run
```

Or modify the sector in `main.py`:
```python
inputs = {
    'sector': 'Technology',
    'current_date': str(datetime.now())
}
```

## 📁 Output

Three files are generated:
- `output/trending_companies.json` - Discovered trending stocks
- `output/research_report.json` - Detailed analysis
- `output/decision.md` - Final recommendation with rationale
- **+ Push notification to your device!**

## 📂 Project Structure

```
stock_picker/
├── output/
│   ├── trending_companies.json
│   ├── research_report.json
│   └── decision.md
├── memory/                          # Persistent memory storage
│   └── long_term_memory_storage.db
├── knowledge/
└── src/stock_picker/
    ├── config/
    │   ├── agents.yaml
    │   └── tasks.yaml
    ├── tools/
    │   ├── __init__.py
    │   └── push_tool.py            # Custom Pushover integration
    ├── crew.py
    └── main.py
```

## 💡 Example Sectors

- Technology
- Healthcare
- Finance
- Energy
- Consumer Goods

## 🎨 Key Features

- **Hierarchical Process**: Manager agent delegates and coordinates
- **Memory Persistence**: Learns from past runs (won't pick same company twice)
- **Real-time Alerts**: Push notifications for instant updates
- **Structured Data**: Type-safe Pydantic models
- **Web Search**: Real-time market data via Serper

## ⚠️ Disclaimer

Stock recommendations are for educational purposes only. This is not financial advice. Always do your own research and consult with a qualified financial advisor before making investment decisions.