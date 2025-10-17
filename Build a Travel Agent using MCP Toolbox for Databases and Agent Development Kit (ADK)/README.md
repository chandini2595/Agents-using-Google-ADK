# Travel Agent with ADK and MCP Toolbox for Databases

## Project Goal

This repository details the architecture and implementation steps derived from the Google Codelab on the Agent Development Kit (ADK) and the MCP Toolbox for Databases.

The primary objective is to create a production-grade, data-grounded AI agent capable of handling complex travel-related queries by securely connecting to and querying a managed PostgreSQL database (Cloud SQL).

## Architecture Overview

The system operates across three secure and distinct layers:

Database Layer (Cloud SQL): The immutable source of truth for hotel and travel data.

Toolbox Layer (MCP Toolbox for Databases): A crucial intermediary service that provides secure, parameterized SQL execution via defined tools, shielding the raw database connection from the LLM.

Agent Layer (ADK): The application hosting the Gemini model. The model acts as a reasoning engine, deciding when a user's request requires the execution of an external function (Tool) hosted by the MCP Server.

## Step-by-Step Codelab Implementation Summary

The codelab is segmented into three logical phases: Infrastructure, Tool Definition, and Agent Integration.

Phase 1: Infrastructure Setup (Cloud SQL)

This phase ensures the data source is provisioned and accessible.

Cloud Project Setup: Create a Google Cloud Project and enable essential APIs (e.g., sqladmin.googleapis.com, run.googleapis.com, aiplatform.googleapis.com).

Cloud SQL Provisioning: Create a PostgreSQL instance (hoteldb-instance) to store the hotel data.

Database Schema & Data:

Connect via Cloud SQL Studio.

Create the hotels table.

Insert sample hotel data (including name, location, price_tier, and booking status).

Phase 2: MCP Toolbox Configuration (Tool Definition)

The MCP Toolbox is configured to translate natural language requests into structured database queries.

Toolbox Installation: Download and install the necessary toolbox binary.

Tool Configuration (tools.yaml): This file defines the connection and the available functions:

```
# Defines the connection to the Cloud SQL instance
sources:
  my-cloud-sql-source:
    kind: cloud-sql-postgres
    # ... connection details (project, instance, user, password)

# Defines the specific functions the agent can call
tools:
  search-hotels-by-name:
    description: Search for hotels based on name.
    statement: SELECT * FROM hotels WHERE name ILIKE '%' || $1 || '%';

  search-hotels-by-location:
    description: Search for hotels based on location. Results are sorted by price.
    statement: |
      SELECT * FROM hotels WHERE location ILIKE '%' || $1 || '%'
      ORDER BY CASE price_tier WHEN 'Midscale' THEN 1 ... END;

toolsets:
  my_first_toolset:
    - search-hotels-by-name
    - search-hotels-by-location
```
Running the Server: Start the local MCP server: ./toolbox --tools_file "tools.yaml".

Phase 3: Agent Development Kit (ADK) Integration

The Agent is built in Python to leverage the MCP Toolbox as its primary data tool.

Agent Script (agent.py): The Agent uses the toolbox-core client to load the defined tools and passes them to the Gemini model.

```
from google.adk.agents import Agent
from toolbox_core import ToolboxSyncClient

# Initialize client to connect to the running MCP Toolbox server
toolbox = ToolboxSyncClient("[http://127.0.0.1:5000](http://127.0.0.1:5000)")

# Load the entire toolset
tools = toolbox.load_toolset('my_first_toolset')

root_agent = Agent(
    name="hotel_agent",
    model="gemini-2.5-flash",
    description="Agent to answer questions about hotels in a city or by name.",
    instruction="You are a helpful agent who must use the tools to answer the user's question.",
    tools=tools, # This is where the magic happens
)



```
Phase 4: Testing and Cloud Deployment

Local Testing: Run the Agent (adk run) alongside the local MCP server to confirm successful tool-call generation, execution, and response grounding.

Cloud Run Deployment (Optional):

Deploy the MCP Toolbox server to a Cloud Run service to get a reliable, external URL.

Update the agent.py script to use this Cloud Run URL.

Deploy the final ADK Agent application to a separate Cloud Run service using adk deploy cloud_run.

🧹 Cleanup

Always ensure you clean up the provisioned Google Cloud resources, including the Cloud SQL instance and Cloud Run services, to manage costs.

🔗 Original Codelab Source

For the full, detailed implementation steps and deep dives into the Gemini CLI integration, refer to the official codelab:

https://codelabs.developers.google.com/travel-agent-mcp-toolbox-adk#0

Youtube: https://youtu.be/WGRPAytqJtU
