# Social-to-Lead Agentic Workflow – AutoStream AI Agent

## Overview
This project implements a conversational AI agent for a SaaS product called AutoStream. The agent can understand user intent, answer product-related queries using a knowledge base, and capture high-intent users as leads through a structured workflow.

## Features
- Intent detection (greeting, pricing inquiry, high-intent)
- Retrieval-based responses using a local JSON knowledge base
- Multi-turn conversation with state management
- Lead capture workflow
- Controlled tool execution

## Tech Stack
- Python 3.11
- LangGraph
- LangChain (light usage)
- JSON (knowledge base)

## How to Run

1. Create a virtual environment:
```bash
python -m venv venv
Activate the environment:
venv\Scripts\activate
Install dependencies:
pip install -r requirements.txt
Run the agent:
python main.py

## Architecture

The agent is implemented using LangGraph, where the workflow is modeled as a graph of nodes. Each node represents a specific task such as intent detection, knowledge retrieval, lead collection, or tool execution.

Based on user input, the agent first identifies intent and routes the conversation accordingly. For pricing-related queries, information is retrieved from a local JSON knowledge base instead of being hardcoded.

When a high-intent user is detected, the system transitions into a lead collection flow. A shared state object is used to maintain context across multiple turns, allowing the agent to collect details such as name, email, and platform step by step.

Once all required information is collected, a tool function is triggered to simulate lead capture. The system ensures that this action only occurs after complete data collection.

This design keeps the system modular, easy to maintain, and suitable for real-world applications.

## WhatsApp Integration (Design)

This project does not currently include WhatsApp integration, but it can be extended using the WhatsApp Business API.

A backend service (such as Flask or FastAPI) can be used to receive incoming messages via webhooks. These messages would be passed to the agent, which processes them using the LangGraph workflow and generates a response.

The response can then be sent back to the user through the WhatsApp API. To support multi-turn conversations, user state can be stored in a database or cache (e.g., Redis), ensuring continuity across interactions.


