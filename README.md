# Databricks Free Edition Demos

This repository contains a selection of demos covering a range of Databricks use cases, all compatible with the Databricks Free Edition.

## Chef Casper's Ghost Kitchen

All demos in this repository use Casper's Ghost Kitchen as a fictional business example.

A ghost kitchen is a commercial cooking facility designed exclusively for delivery orders: no dining room, just kitchen space optimized for fulfilling online orders. Multiple restaurant brands often operate from a single ghost kitchen facility.

This business model generates rich operational event data throughout the order lifecycle, from initial order placement, through kitchen preparation, driver assignment and pickup, real-time delivery tracking with GPS coordinates, to final delivery confirmation. Each order creates multiple timestamped events with detailed JSON payloads capturing everything from kitchen progress to driver location pings.

Casper's Ghost Kitchen processes hundreds of orders daily across multiple virtual restaurant brands, creating realistic datasets perfect for demonstrating data engineering, analytics, and AI applications with Databricks.

## Prerequisites

- Databricks Free Edition account
- Basic familiarity with Python and SQL
- No external data sources required: sample data is included!

## Getting Started

Getting started with these demos is simple. You just need to sign up for Databricks Free Edition, and then clone this repository.

### Sign up for Databricks Free Edition

You can sign up for Databricks Free Edition [here](https://login.databricks.com/?dbx_source=docs&intent=CE_SIGN_UP). To learn more about Free Edition, see the [Databricks Docs](https://docs.databricks.com/aws/en/getting-started/free-edition).

### Clone this repository

From the home page of your Databricks workspace, click the `+ New` button in the top right corner, then, under "more", select "Git folder".

![New Git Folder](images/new_git_folder.png)

Enter the URL of this repository (`https://github.com/chefcaspers/databricksfree`) and then click "Create Git folder". This will clone the repository into a new folder in your workspace.

### Run the demos

Each notebook is a standalone demo that you can run independently. However, for the complete Databricks experience—from raw data ingestion to intelligent AI agents—follow this recommended sequence:

1. **[Lakeflow](lakeflow.ipynb)**: Start here to build your data foundation. Transform raw JSON events into a clean, queryable Medallion architecture using Declarative Pipelines.
2. **[AI/BI Genie](ai_bi_genie.ipynb)**: With your data ready, explore it naturally. Ask questions in plain English and let Genie generate SQL queries and visualizations automatically.
3. **[Agents](agents.ipynb)**: Build AI agents that can intelligently query your data and execute actions through Unity Catalog functions.
