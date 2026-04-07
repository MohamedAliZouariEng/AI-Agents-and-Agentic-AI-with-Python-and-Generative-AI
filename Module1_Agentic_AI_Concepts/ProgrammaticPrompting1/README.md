# 🤖 Programmatic Prompting for AI Agents

[![Python 3.12+](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![LiteLLM](https://img.shields.io/badge/LiteLLM-Groq-green.svg)](https://github.com/BerriAI/litellm)

## 📋 Overview

This module introduces the fundamental concepts of **programmatic prompting** and **memory management** for building AI agents. You'll learn how to move from manual prompt-response cycles to automated agent loops that can make decisions and take actions programmatically.

### 🎯 Key Concepts Covered

- **Programmatic Prompting** - Automating the prompt-response cycle that forms the foundation of the Agent Loop
- **Memory Management** - Controlling what information persists between iterations for maintaining context
- **System Messages** - Programming AI agents through system-level instructions
- **Structured Data Integration** - Using JSON and other formats to pass information to LLMs

## 🚀 Getting Started

### Prerequisites

- Python 3.12 or higher
- A Groq API key (free tier available at [console.groq.com](https://console.groq.com))

### 📦 Installation

1. **Clone the repository**
```bash
git clone https://github.com/MohamedAliZouariEng/AI-Agents-and-Agentic-AI-with-Python-and-Generative-AI.git
cd AI-Agents-and-Agentic-AI-with-Python-and-Generative-AI/Module1_Agentic_AI_Concepts/ProgrammaticPrompting1/
```

2. **Create and activate a virtual environment**
```bash
python3 -m venv venv
source venv/bin/activate 
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Set up environment variables**
```bash
# Create .env file in the ProgrammaticPrompting1/ directory
echo "GROQ_API_KEY=your_groq_api_key_here" > .env
```

> 💡 **Note**: Replace `your_groq_api_key_here` with your actual Groq API key

## 📁 Project Structure

```
ProgrammaticPrompting1/
├── 📓 ProgrammaticPrompting1.ipynb   # Main Jupyter notebook
├── 📄 requirements.txt                # Python dependencies
├── 🔒 .env                           # Environment variables (create this)
└── 📖 README.md                      # This file
```



## 🎓 What You'll Learn

### 1️⃣ Basic Programmatic Prompting
Learn how to send prompts to LLMs using LiteLLM's `completion` function and understand the ChatML format with system, user, and assistant roles.

### 2️⃣ System Message Programming
Discover how to "program" AI agents through system messages to control behavior and response patterns.

### 3️⃣ Structured Data Integration
Master passing JSON and other structured data to LLMs for complex instructions and API result processing.

## 🔍 Examples

### Basic Completion
```python
from litellm import completion

messages = [
    {"role": "system", "content": "You are an expert software engineer"},
    {"role": "user", "content": "Write a function to swap dictionary keys and values"}
]

response = completion(
    model="groq/llama-3.3-70b-versatile",
    messages=messages,
    max_tokens=1024
)
```

### Customer Service Agent with System Instructions
```python
messages = [
    {"role": "system", "content": "Always suggest turning the device off and on"},
    {"role": "user", "content": "How do I fix my internet?"}
]
```

### JSON Specification Integration
```python
code_spec = {
    'name': 'swap_keys_values',
    'description': 'Swaps keys and values in a dictionary',
    'params': {'d': 'A dictionary with unique values'}
}

messages = [
    {"role": "user", "content": f"Implement: {json.dumps(code_spec)}"}
]
```

## 🎯 Learning Outcomes

By the end of this module, you'll be able to:

- ✅ Send prompts programmatically to LLMs
- ✅ Understand and manage conversation memory
- ✅ Use system messages to control AI behavior
- ✅ Pass structured data (JSON) to LLMs
- ✅ Build the foundation for autonomous agent loops

## 📚 References

- **Course**: [AI Agents and Agentic AI with Python and Generative AI](https://www.coursera.org/learn/ai-agents-python) on Coursera
- **LiteLLM Documentation**: [https://docs.litellm.ai/](https://docs.litellm.ai/)
- **Groq Documentation**: [https://console.groq.com/docs](https://console.groq.com/docs)
