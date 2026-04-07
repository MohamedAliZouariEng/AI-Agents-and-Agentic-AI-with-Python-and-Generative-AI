# 📖 Build Your First AI Agent

[![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![Groq](https://img.shields.io/badge/Groq-LLaMA%203.3-orange.svg)](https://groq.com/)

> Learn how to build a simple yet powerful AI agent from scratch using Python and Groq's LLaMA model. This project demonstrates the core concepts of agentic AI - where an LLM orchestrates tools and makes decisions dynamically.

## 🎯 Overview

This repository contains a complete implementation of a basic AI agent that can:
- 📁 List files in a directory
- 📖 Read file contents
- 🤔 Answer questions about files
- 🔄 Dynamically decide which actions to take

The agent follows the **ReAct (Reasoning + Acting)** paradigm, iteratively deciding what to do based on previous results and current context.

## 🏗️ Project Structure

```
Module1_Agentic_AI_Concepts/Build_Agent/
├── Build_Agent.ipynb          # Main Jupyter notebook with agent implementation
├── file1.txt                  # Sample file (content: "I'm happy")
├── file2.txt                  # Sample file (content: "I'm sad")
├── .env                       # Environment variables (GROQ_API_KEY)
├── requirements.txt           # Python dependencies
└── README.md                  # This file
```

## 🚀 Quick Start

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/MohamedAliZouariEng/AI-Agents-and-Agentic-AI-with-Python-and-Generative-AI.git
cd AI-Agents-and-Agentic-AI-with-Python-and-Generative-AI/Module1_Agentic_AI_Concepts/Build_Agent
```

### 2️⃣ Create and Activate Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate 
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Set Up Your API Key

Create a `.env` file in the `Build_Agent/` directory:

```bash
GROQ_API_KEY=your_groq_api_key_here********************************
```

> 💡 **Get your API key**: Sign up at [Groq Console](https://console.groq.com/) to obtain your free API key.


## 🧠 How It Works

The agent follows a **6-step iterative loop**:

```
┌─────────────────────────────────────────────────────────┐
│                    AGENT LOOP                           │
│                                                          │
│  1. Construct Prompt ──► 2. Generate Response          │
│         ▲                        │                      │
│         │                        ▼                      │
│  6. Decide Continue        3. Parse Action              │
│         ▲                        │                      │
│         │                        ▼                      │
│  5. Update Memory ◄──────── 4. Execute Action           │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

### Available Tools

| Tool | Description | Example |
|------|-------------|---------|
| `list_files()` | Lists all files in current directory | Returns `['file1.txt', 'file2.txt']` |
| `read_file(file_name)` | Reads content of a specific file | Returns file content as string |
| `terminate(message)` | Ends the agent loop with a summary message | Prints message and exits |

### Example Interaction

```
User: What files are here and what do they say?

Agent thinking...
Agent response: {"tool_name": "list_files", "args": {}}
Action result: ['file1.txt', 'file2.txt', '.env', 'Build_Agent.ipynb']

Agent thinking...
Agent response: {"tool_name": "read_file", "args": {"file_name": "file1.txt"}}
Action result: "I'm happy"

Agent thinking...
Agent response: {"tool_name": "read_file", "args": {"file_name": "file2.txt"}}
Action result: "I'm sad"

Agent thinking...
Agent response: {"tool_name": "terminate", "args": {"message": "Found 2 files. file1.txt says 'I'm happy', file2.txt says 'I'm sad'."}}
Operation completed
```

## 🔧 Key Components

### 1. Agent Rules (System Prompt)
Defines the agent's behavior, available tools, and response format:
```python
agent_rules = [{
    "role": "system",
    "content": """
    You are an AI agent that can perform tasks by using available tools.
    Available tools: list_files(), read_file(), terminate()
    Respond in JSON format within ```action blocks.
    """
}]
```

### 2. Memory Management
The agent maintains conversation history to make informed decisions:
```python
memory.extend([
    {"role": "assistant", "content": response},
    {"role": "user", "content": json.dumps(result)}
])
```

### 3. Action Parsing
Extracts structured actions from LLM responses:
```python
def parse_action(response: str) -> Dict:
    # Extracts JSON from ```action blocks
    # Returns {"tool_name": "...", "args": {...}}
```


## 🔍 References

This project is based on the course:
- **[AI Agents and Agentic AI with Python and Generative AI](https://www.coursera.org/learn/ai-agents-python)** on Coursera

Additional resources:
- [Groq Documentation](https://console.groq.com/docs/quickstart)
- [LiteLLM Documentation](https://docs.litellm.ai/)
