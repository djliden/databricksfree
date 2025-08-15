# Build an End-to-End Data Platform with Databricks Free Edition

**Experience the complete Databricks platform—from raw data ingestion to AI agents—using realistic business data.**

## What You'll Build

Transform from raw JSON events to intelligent AI agents in three (for now) hands-on demos:
- **Data Engineering**: Medallion architecture with streaming pipelines using Delta Live Tables
- **Analytics**: Natural language data exploration with AI/BI Genie  
- **AI Agents**: Intelligent assistants that query data and execute business actions

All using Chef Casper's Ghost Kitchen—a realistic fictional business generating rich operational event data from order placement to delivery completion.

## 🚀 Quick Start (2 Steps)

**Step 1:** [Sign up for Databricks Free Edition](https://login.databricks.com/?dbx_source=docs&intent=CE_SIGN_UP)

**Step 2** From the home page of your Databricks workspace, click the `+ New` button in the top right corner, then, under "more", select "Git folder".

![New Git Folder](images/new_git_folder.png)

Enter the URL of this repository (`https://github.com/chefcaspers/databricksfree`) and then click "Create Git folder". This will clone the repository into a new folder in your workspace.

**Step 3:** Step through the notebooks in this order for the best experience:
1. **[lakeflow.ipynb](lakeflow.ipynb)** - Build your data foundation
2. **[ai_bi_genie.ipynb](ai_bi_genie.ipynb)** - Explore data with natural language  
3. **[agents.ipynb](agents.ipynb)** - Create intelligent AI agents

_Note:_ Though we recommend working through the notebooks in the order above, later notebooks do not depend on earlier ones, so you can run them in whatever order you choose.

## About the Demo Data

Chef Casper's Ghost Kitchen is a delivery-only facility processing orders from multiple virtual restaurant brands. This generates realistic operational event data throughout the complete order lifecycle—from placement through kitchen prep, driver assignment, real-time GPS tracking, to final delivery confirmation.

Perfect for demonstrating real-world data engineering, analytics, and AI applications with Databricks.

## Prerequisites

- Basic familiarity with Python and SQL
- All sample data included—no external sources needed!
