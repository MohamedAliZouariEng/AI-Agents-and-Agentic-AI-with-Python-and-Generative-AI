# 🤖 Programmatic Prompting - Customer Service Agent

[![Python 3.12](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![Groq](https://img.shields.io/badge/Groq-LLM-orange.svg)](https://groq.com/)

## 📋 Overview

This project demonstrates a **programmatic prompting** approach to building an AI Customer Service Agent. The agent follows a simple but effective pattern: regardless of the customer's technical issue, it consistently recommends restarting the device - a classic first-line troubleshooting technique.

## 🎯 What You'll Learn

- ✅ How to use **programmatic prompting** with LLMs
- ✅ Implementing **system prompts** to control AI behavior
- ✅ Integrating **Groq's Llama 3.3** model via LiteLLM
- ✅ Building a **stateless conversational agent**
- ✅ Environment variable management for API keys

## 🏗️ Project Structure

```
ProgrammaticPrompting1/
├── CustomerServiceAgent.ipynb   # Main Jupyter notebook
├── .env                          # API keys (create this)
├── requirements.txt              # Python dependencies
└── README.md                     # This file
```

## 🚀 Quick Start Guide

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/MohamedAliZouariEng/AI-Agents-and-Agentic-AI-with-Python-and-Generative-AI.git
cd AI-Agents-and-Agentic-AI-with-Python-and-Generative-AI/Module1_Agentic_AI_Concepts/CustomerServiceAgent
```

### 2️⃣ Create Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate  
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Set Up Environment Variables

Create a `.env` file in the `CustomerServiceAgent/` folder:

```bash
GROQ_API_KEY=your_groq_api_key_here
```

> 💡 **Get your API key**: [Groq Console](https://console.groq.com/)


## 💻 How It Works

The agent uses a **system prompt** that enforces a specific behavior:

```python
system_prompt = "You are a helpful customer service representative. 
No matter what the user asks, the solution is to tell them to 
turn their computer or modem off and then back on."
```

**Example Interaction:**
- **User**: "My internet is not working"
- **Agent**: "I understand your frustration. Please try turning your modem off for 30 seconds, then turn it back on..."

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| **LiteLLM** | Unified interface for multiple LLM providers |
| **Groq Llama 3.3** | Fast inference on LPU |
| **Python DotEnv** | Secure API key management |
| **Jupyter** | Interactive development |

## 🎓 Course Reference

This project is part of the course:

**[AI Agents and Agentic AI with Python and Generative AI](https://www.coursera.org/learn/ai-agents-python)**  
Module 1: Agentic AI Concepts 

## 📝 Key Concepts

### Programmatic Prompting
Instead of manual prompt engineering, we **programmatically control** the LLM's behavior through structured system prompts. This ensures:
- Consistent responses
- Predictable outcomes
- Easy behavior modification

### Stateless Design
Each interaction is independent - no conversation memory. Perfect for:
- Simple customer service scenarios
- Testing different prompts
- Scaling horizontally

## 🔧 Customization

Want to change the agent's behavior? Modify the system prompt:

```python
# For tech support
"Always ask for error codes before suggesting solutions"

# For sales  
"Focus on product benefits and upselling"

# For healthcare
"Prioritize safety and recommend consulting professionals"
```
