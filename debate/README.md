# ⚔️ Debate

> AI Agents Engaging in Structured Debates

A debate simulation where one agent argues both sides of a motion, and a separate judge agent decides the winner based purely on argument merit.

## 🎯 Overview

This crew simulates a formal debate:
1. **Proposer** presents arguments FOR the motion
2. **Opposer** presents arguments AGAINST the motion
3. **Judge** evaluates and decides the winner

The same debater agent argues both sides, while an impartial judge (using a different LLM) makes the final decision.

## 🤖 Agents

| Agent | Role | LLM |
|-------|------|-----|
| **Debater** | Argues both FOR and AGAINST | `gpt-4o-mini` |
| **Judge** | Decides the winner | `claude-3-7-sonnet-latest` |

## 📋 Tasks

| Task | Description | Agent | Output |
|------|-------------|-------|--------|
| **propose** | Argue in favor of the motion | Debater | `output/propose.md` |
| **oppose** | Argue against the motion | Debater | `output/oppose.md` |
| **decide** | Review arguments and decide winner | Judge | `output/decide.md` |

## 🔄 Workflow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   PROPOSE   │ ──▶ │   OPPOSE    │ ──▶ │   DECIDE    │
│  (Debater)  │     │  (Debater)  │     │   (Judge)   │
│ GPT-4o-mini │     │ GPT-4o-mini │     │Claude Sonnet│
└─────────────┘     └─────────────┘     └─────────────┘
```

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- OpenAI API key
- Anthropic API key

### Installation

```bash
cd debate
pip install crewai crewai-tools
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

Or modify the motion in `main.py`:
```python
inputs = {
    'motion': 'There needs to be strict laws to regulate LLMs',
}
```

## 📁 Output

Three markdown files are generated:
- `output/propose.md` - Arguments FOR the motion
- `output/oppose.md` - Arguments AGAINST the motion
- `output/decide.md` - Judge's decision and reasoning

## 📂 Project Structure

```
debate/
├── output/
│   ├── propose.md
│   ├── oppose.md
│   └── decide.md
├── knowledge/
└── src/debate/
    ├── config/
    │   ├── agents.yaml
    │   └── tasks.yaml
    ├── tools/
    │   └── custom_tool.py
    ├── crew.py
    └── main.py
```

## 💡 Example Motions

- "There needs to be strict laws to regulate LLMs"
- "Remote work is more productive than office work"
- "AI will create more jobs than it destroys"
- "Social media does more harm than good"

## 🎨 Key Features

- **Multi-LLM Setup**: Uses GPT-4o-mini for debating and Claude for judging
- **Impartial Judgment**: Judge decides purely on argument merit
- **Structured Output**: Clean markdown files for each debate stage