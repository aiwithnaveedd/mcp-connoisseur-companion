# Connoisseur Companion — MCP Restaurant Guide Host Application 🍽️

An end-to-end **Model Context Protocol (MCP) host application** that connects a Gradio chat interface with IBM WatsonX LLMs (`ibm/granite-4-h-small`) to query structured and unstructured California restaurant data.

Using a **ReAct (Reason + Act) agent loop**, the application dynamically discovers MCP tools at runtime, executes tool calls, and generates detailed natural language responses.

---

## 🌟 Features

* **MCP Dynamic Discovery:** Discovers exposed server tools and resource endpoints at runtime over STDIO.
* **ReAct Agent Loop:** Iteratively calls tools, processes their outputs through `ToolMessage`, and synthesizes final natural language answers.
* **Gradio Chat UI:** Provides an interactive chat interface featuring quick-start prompt buttons and visual feedback.
* **Multi-Source Data Integration:** Queries structured restaurant metadata, raw-text culinary guide excerpts, and augmented user reviews.
* **LLM-Powered Responses:** Uses IBM WatsonX and the Granite model to interpret queries and generate contextual responses.
* **Tool Execution:** Dynamically converts MCP tool schemas into LLM-compatible tool definitions.

---

## 🚀 Quick Start & Setup

### 1. Prerequisites

Ensure you have **Python 3.10 or later** installed.

### 2. Create a Virtual Environment

Create and activate an isolated Python virtual environment:

```bash
pip install virtualenv
virtualenv .venv
```

On macOS/Linux:

```bash
source .venv/bin/activate
```

On Windows (PowerShell):

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

Install the required Python libraries:

```bash
pip install gradio==6.9.0 fastmcp==3.1.0 langchain-ibm==1.0.4 langchain-core==1.2.18
```

---

## 🔑 Environment Variables

Configure your IBM WatsonX project credentials.

### macOS/Linux

```bash
export WATSONX_AI_PROJECT_ID="your-watsonx-project-id"
```

Alternatively, you can use:

```bash
export WATSONX_PROJECT_ID="your-watsonx-project-id"
```

Replace the placeholder with your actual WatsonX project ID.

**Note:** Depending on your WatsonX configuration, you may also need to configure your IBM Cloud API key and other required credentials.

---

## 📂 Download Required Data & Server Scripts

Download the structured restaurant data, unstructured culinary map, augmented user reviews, and MCP server script.

### 1. Structured Restaurant Data

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/clYj6XUC9urkUzWtiDH0Cw/structured-restaurant-data.json
```

### 2. Unstructured California Culinary Map

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/taf6n5kHS3H2ZLRf9tihFw/California-Culinary-Map.txt
```

### 3. Augmented User Reviews

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/q5CWrWtux9-NmnkiWOrQBw/augmented-user-review.json
```

### 4. MCP Server Script

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/ql0xua4ET4XmQCOpR1lrNg/server.py
```

Ensure that all downloaded files are available in the project directory before launching the application.

---

## ▶️ Run the Application

Launch the Gradio web application:

```bash
python app.py
```

Alternatively, launch it using the Gradio CLI:

```bash
gradio app.py
```

Once the application starts, open the local URL displayed in your terminal to interact with the restaurant guide.

---

## 🛠️ MCP Tools Exposed & Used

The host application dynamically converts MCP tool schemas into LLM-compatible definitions and invokes the following tools.

### 1. `get_restaurant_info`

Looks up restaurants by name and returns structured information, including:

* Restaurant name
* Cuisine
* Rating
* Price range
* Signature dishes

### 2. `recommend_by_vibe`

Performs keyword-based searches across structured vibe tags and unstructured text excerpts to recommend restaurants based on their mood and atmosphere.

Example queries:

* Recommend a romantic restaurant.
* Find a moody, upscale dining experience.
* Suggest a restaurant with a relaxed atmosphere.

### 3. `get_review`

Retrieves restaurant review records, including:

* User feedback
* Ratings
* Visit dates
* Additional review context

---

## 🧠 Architecture Overview

The application combines an MCP server, an LLM-powered agent, and a Gradio interface.

1. **User Input:** The user submits a restaurant-related question through the Gradio chat interface.
2. **LLM Reasoning:** The WatsonX Granite model interprets the query and determines whether tools are needed.
3. **MCP Tool Discovery:** The host discovers available tools and their schemas from the MCP server.
4. **Tool Execution:** The agent invokes the appropriate tools through the MCP client over STDIO.
5. **Observation Processing:** Tool results are processed and returned to the agent.
6. **Final Response:** The LLM generates a contextual natural language response displayed in the Gradio interface.

---

## 🛠️ Technologies Used

* **Python**
* **Model Context Protocol (MCP)**
* **FastMCP**
* **IBM WatsonX**
* **IBM Granite (`ibm/granite-4-h-small`)**
* **LangChain Core**
* **LangChain IBM**
* **Gradio**
* **ReAct Agent Architecture**
* **STDIO Transport**
* **JSON Data Processing**

---

## 👨‍💻 Author & Acknowledgments

**Abdul Fatir | Data Scientist @ IBM**

Author profile: [Abdul Fatir on Skills Network](https://author.skills.network/instructors/abdul_fatir)
