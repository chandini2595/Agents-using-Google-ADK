# From Prototypes to Agents with ADK

This repository contains the completed code for the **"From Prototypes to Agents with ADK"** Codelab, which guides developers on transforming a simple AI prompt-based prototype into a fully functional, autonomous AI Agent using the **Agent Development Kit (ADK)**.

The project demonstrates building a single-agent system that leverages Google's Gemini model and the ADK framework to solve a real-world task: generating and storing a professional document.

---

## 🚀 Project Goal: Renovation Proposal Agent

The primary objective is to build an intelligent agent that can autonomously generate a comprehensive **Kitchen Renovation Proposal Document** based on a user request and store the output in Google Cloud Storage.

### Key Learnings

By completing this codelab, you will learn how to:

* Define and configure a goal-based **AI Agent** using the Vertex AI Agent Development Kit (ADK).
* Structure a Python project for agentic applications (`agent.py`, `.env`, `requirements.txt`).
* Integrate and use **Tools** within an agent (e.g., a tool for saving a file to **Google Cloud Storage**).
* Implement a root agent that acts as an **orchestrator** for a single-agent system.
* Set up the development environment in **Google Cloud Shell** and activate the agent.

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following:

1.  A **Google Cloud Project** with **billing enabled**.
2.  Access to **Google Cloud Shell** (recommended for environment consistency).
3.  The **Vertex AI API** enabled in your Google Cloud Project.
4.  A **Google Cloud Storage Bucket** created to store the agent's output.

---

## ⚙️ Setup and Installation

Follow these steps in your Cloud Shell terminal to set up the environment and install the necessary dependencies.

### 1. Create and Activate Virtual Environment

```bash
# Create a root directory for your agentic applications
mkdir agentic-apps
cd agentic-apps

# Create the project directory
mkdir renovation-agent
cd renovation-agent

# Create a Python virtual environment
python -m venv .venv

# Activate the virtual environment
source .venv/bin/activate
```
It looks like the markdown structure was slightly broken in the user's prompt (specifically at steps 2 and 3 of the Setup and Installation section and near the --- separator).

Here is the complete, corrected, and well-structured GitHub README for the "From Prototypes to Agents with ADK" codelab, all combined into a single markdown block.

Markdown

# From Prototypes to Agents with ADK: Kitchen Renovation Agent 🏠

This repository contains the completed code and instructions for the **"From Prototypes to Agents with ADK"** Codelab. The goal of this lab is to guide developers in transitioning a simple AI prompt-based prototype into a fully functional, autonomous **AI Agent** using the **Vertex AI Agent Development Kit (ADK)**.

The project demonstrates building a single-agent system designed to handle the complex task of generating and storing a professional document.

---

## 🚀 Project Goal

The primary objective is to build an intelligent agent that can autonomously generate a comprehensive **Kitchen Renovation Proposal Document** based on a user request and store the output in Google Cloud Storage.

### Key Learnings

By completing this codelab, you will learn how to:

* Define and configure a goal-based **AI Agent** using the Vertex AI Agent Development Kit (ADK).
* Structure a Python project for agentic applications (`agent.py`, `.env`, `requirements.txt`).
* Integrate and use **Tools** within an agent (specifically, a tool for saving a file to **Google Cloud Storage**).
* Implement a root agent that acts as an **orchestrator** for a single-agent system.
* Set up the development environment in **Google Cloud Shell** and activate the agent.

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following:

1.  A **Google Cloud Project** with **billing enabled**.
2.  Access to **Google Cloud Shell** (recommended for environment consistency).
3.  The **Vertex AI API** enabled in your Google Cloud Project.
4.  A **Google Cloud Storage Bucket** created to store the agent's proposal documents.

---

## ⚙️ Setup and Installation

Follow these steps in your Cloud Shell terminal to set up the environment and install the necessary dependencies.

### 1. Create and Activate Virtual Environment

```bash
# Create a root directory for your agentic applications
mkdir agentic-apps
cd agentic-apps

# Create the project directory
mkdir renovation-agent
cd renovation-agent

# Create a Python virtual environment
python -m venv .venv

# Activate the virtual environment
source .venv/bin/activate
```
2. Install ADK and Dependencies
Install the Agent Development Kit and any other required libraries.
```
# Install the Google Agent Development Kit
pip install google-adk

# If you have specific dependencies for your project, list them here:
# pip install -r requirements.txt
```
3. Configure Environment Variables

Create a file named .env in your project root (renovation-agent/) to configure access keys and project settings.
```
# Example .env file content:

# 1. Google Cloud Configuration
# Your Google Cloud Project ID
PROJECT_ID="your-gcp-project-id"

# 2. Agent/Model Configuration
# The LLM model to use (e.g., Gemini 2.5 Flash)
MODEL_NAME="gemini-2.5-flash"

# 3. Tool Configuration (for the GCS storage tool)
# The Cloud Storage Bucket where the proposal will be saved
GCS_BUCKET_NAME="your-proposal-storage-bucket"
```

Note: Ensure your Google Cloud services are configured to allow the agent to access the specified resources (e.g., Storage Object Creator role for the service account running the agent). This is critical for the agent's file storage Tool to function correctly.

Youtube Video: https://youtu.be/NsMJ_b4rp7s


