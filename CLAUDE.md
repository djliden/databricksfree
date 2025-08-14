# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repository contains Databricks Free Edition demos for "Chef Casper's Ghost Kitchen" - a fictional business generating realistic operational event data. All demos are designed to run on Databricks Free Edition without external dependencies.

## Key Architecture

### Data Architecture - Medallion Pattern
The codebase implements a complete medallion architecture using Delta Live Tables:

- **Bronze Layer**: Raw JSON events ingested via Auto Loader into `all_events` table
- **Silver Layer**: Cleaned and transformed data with exploded order items in `dlt_order_items` 
- **Gold Layer**: Business-ready aggregated tables for analytics and AI applications

### Unity Catalog Structure
Default catalog hierarchy:
```
gk_demo/
  default/
    raw_data/          (volume for source data)
    all_events         (bronze table)
    dlt_order_items    (silver table)
    dlt_order_header   (gold table)
    dlt_item_sales_day (gold table)
    ...
```

### Core Components

1. **utils/utils.py** - Shared utilities for catalog/volume setup, data initialization, and table creation
2. **pipelines/order_items_dlt/transformations/transformation.py** - DLT pipeline definitions using streaming patterns
3. **notebooks/** - Standalone demo notebooks following the recommended sequence

## Notebook Execution Sequence

The demos should be run in this order for the complete Databricks experience:

1. **lakeflow.ipynb** - Build data foundation with medallion architecture using Declarative Pipelines
2. **ai_bi_genie.ipynb** - Natural language data exploration with AI/BI Genie  
3. **agents.ipynb** - Build AI agents that query data and execute actions via Unity Catalog functions

## Development Patterns

### Data Processing
- Use Delta Live Tables (DLT) for streaming ETL pipelines
- Implement watermarking for streaming aggregations (typically 3 hours)
- Partition tables by date columns for performance (`order_day`, `day`, `hour_ts`)
- Use `approx_count_distinct()` for scalable distinct counts in streaming contexts

### AI/ML Development  
- Unity Catalog functions serve as agent tools (e.g., `get_order_details`, `get_location_timings`)
- MLflow for model lifecycle management, evaluation, and deployment
- LangGraph for multi-step agent workflows
- Custom instructions in AI/BI Genie for business logic encoding

### Utilities Usage
Common initialization pattern from any notebook:
```python
from utils.utils import setup_catalog_and_volume, copy_raw_data_to_volume, initialize_events_table
setup_catalog_and_volume(spark)
copy_raw_data_to_volume()  
initialize_events_table(spark)
```

## Data Schema Patterns

### Event Stream Structure
Raw events contain:
- `order_id`, `gk_id`, `location`, `event_type`, `ts` (timestamp)
- `body` (JSON) with order details including items array for order_created events

### Item Schema (within order bodies)
```python
item_schema = StructType([
    StructField("id", IntegerType()),
    StructField("category_id", IntegerType()), 
    StructField("menu_id", IntegerType()),
    StructField("brand_id", IntegerType()),
    StructField("name", StringType()),
    StructField("price", DoubleType()),
    StructField("qty", IntegerType())
])
```

## File Organization

- `data/` - Sample parquet files for dimension tables and raw events (JSON.gz)
- `utils/` - Shared Python utilities and order generation tools  
- `pipelines/` - DLT pipeline definitions
- `notebooks/` - Additional specialized notebooks
- `dashboards/` - Dashboard definitions
- `images/` - Screenshot assets organized by demo type

## Configuration Defaults

Key constants defined in `utils/utils.py`:
- Catalog: `gk_demo`  
- Schema: `default`
- Volume: `raw_data`
- Primary events table: `gk_demo.default.all_events`