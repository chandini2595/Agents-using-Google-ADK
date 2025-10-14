
# 🤖 Agent Development Kit (ADK): Building Empowered Agents with Tools
## 🎯 Project Overview
This document serves as a comprehensive reference and summary for the Google Codelab on the Agent Development Kit (ADK), focusing specifically on Function Calling, or "Tools."

The goal is to demonstrate how to equip a Large Language Model (LLM) agent with the ability to execute external code or API calls intelligently. This process transforms a standard text-generating agent into a grounded, actionable system capable of performing real-world tasks.

## ✨ Core Functionality: Tool Empowerment
The central theme is the integration of external functions into the agent pipeline.

## Key Concepts

<img width="777" height="527" alt="image" src="https://github.com/user-attachments/assets/a918ee26-e068-49ba-b996-1ec61c3cc46f" />

## 🛠️ Codelab Walkthrough (The Process)
The codelab illustrates the tool integration process through a sequential flow:

Environment Setup: Setting up the necessary SDKs, handling authentication, and preparing the development environment.

Creating a Tool: Defining a sample utility function (e.g., get_current_weather) and crafting its corresponding Tool definition schema.

Initializing the Agent: Instantiating the ADK Agent, passing the list of available tool definitions directly to its configuration.

Testing Tool Use: Sending a query that necessitates an external action (e.g., "What is the weather like in Seattle this afternoon?").

Observing the Workflow: Analyzing the three-part interaction: LLM generates call → Function executes → Result is fed back to LLM.

Refinement: Iterating on the tool's description and the agent's system prompts to improve the reliability and accuracy of the tool-selection logic.

## 🔗 Original Codelab Source : https://codelabs.developers.google.com/devsite/codelabs/build-agents-with-adk-empowering-with-tools#0

Youtube: https://youtu.be/QAZjSFbzncI
