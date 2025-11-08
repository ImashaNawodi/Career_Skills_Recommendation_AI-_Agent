
## Career Skills Recommendation AI Agent

## Overview

The **Career Skills Recommendation AI Agent** is a Python-based AI tool designed to help professionals identify their existing skills from a resume or LinkedIn profile and recommend **new, trending skills** to advance their careers. The agent combines **skill extraction**, **job market analysis**, and **AI-powered recommendations** to provide actionable insights.

This agent is built using **LangChain**, **OpenAI’s GPT models**, and live job data from **Adzuna API**.

---

## Features

1. **Skill Extraction**

   * Automatically extracts professional skills and technologies from a user-provided profile text or resume.
   * Example: SQL, Python, Power BI, dashboards, data analysis.

2. **Job Market Trend Analysis**

   * Fetches live job descriptions from Adzuna based on a chosen job keyword (e.g., "data").
   * Identifies trending skills mentioned in current job postings.

3. **Career Skill Recommendations**

   * Compares existing skills with trending skills in the job market.
   * Suggests new skills to learn for career growth.
   * Provides overlap and missing skills in a clear format.

4. **Interactive Agent**

   * Uses **LangChain Agents** with multiple tools for step-by-step reasoning.
   * Tools include:

     * `Skill Extractor`
     * `Job Market Trend Analyzer`

---

## Tech Stack

* **Python 3.12**
* **LangChain** – for AI agent orchestration
* **OpenAI GPT-3.5 / GPT-5** – for NLP and reasoning
* **Adzuna API** – for live job market data
* **Colab / Local environment** – for execution

---

## Setup Instructions

### 1. Install Dependencies

```bash
pip install langchain langchain-openai chromadb requests beautifulsoup4 fastapi uvicorn
```

### 2. Set API Keys

**OpenAI API Key**:

```python
import os
from google.colab import userdata
os.environ["OPENAI_API_KEY"] = userdata.get('OPENAI_API_KEY')
```

**Adzuna API Keys**:

1. Register at [Adzuna API](https://developer.adzuna.com/)
2. Get your **App ID** and **App Key**
3. Add them to Colab secrets:

```
YOUR_APP_ID = <your_real_app_id>
YOUR_APP_KEY = <your_real_app_key>
```

```python
app_id = os.environ.get("YOUR_APP_ID")
app_key = os.environ.get("YOUR_APP_KEY")
```

### 3. Run the Agent

```python
profile_text = """
I am a data analyst with 3 years of experience in SQL, Power BI, and Python.
I have worked on dashboards, data cleaning, and reporting.
"""

response = agent.invoke(f"Analyze this profile and recommend new career skills: {profile_text}")
print(response)
```

---

## How It Works

1. **Skill Extraction Tool**

   * Extracts skills from the profile text using the LLM.

2. **Job Market Trend Analyzer Tool**

   * Fetches live job postings from Adzuna.
   * Analyzes descriptions to find trending skills.

3. **Agent Workflow**

   * The agent orchestrates both tools sequentially:

     1. Extract existing skills.
     2. Fetch trending skills.
     3. Compare and recommend new skills.

4. **Output Example**

```
Trending skills you already have: [SQL, Python, Power BI]
Skills to learn next: [AI, Cloud Computing, Data Engineering, Cybersecurity]
```

---

## Notes

* Ensure your **Adzuna API keys** are correct; otherwise, the agent will throw HTTP errors.
* Input profile text can be **any resume or LinkedIn-style summary**.
* You can change the job search keyword in `get_trending_skills_from_api(query="data")` to target different domains.

---


