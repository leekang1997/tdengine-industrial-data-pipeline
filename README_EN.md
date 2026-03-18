# TDengine-Industrial-Data-Pipeline

[中文](./README.md) | [English](./README_EN.md)

`TDengine-Industrial-Data-Pipeline` is an industrial time-series data engineering toolkit covering TDengine schema creation, data ingestion, sequence splitting, spatio-temporal table construction, and training-data export.

## Project Positioning

Industrial time-series data usually comes with several challenges:

- messy upstream sources
- inconsistent fields
- mixed time granularity
- both temporal and spatial features need to be preserved
- downstream consumers often include training and diagnosis pipelines

This project aims to systematize the path from raw industrial data to TDengine tables, engineered features, and SFT-ready samples.

## Current Capabilities

- TDengine schema creation
- industrial data ingestion into TDengine
- time-table, space-table, and spatio-temporal table construction
- feature engineering and sequence slicing
- JSON / SFT training-data export

## Prerequisites

This repository does not replace `TDengine` itself. It is a data-governance and sample-building layer built on top of `TDengine`.

Before using it, you should already have:

1. a working `TDengine` installation
2. permission to access the target database
3. a clear understanding of the raw field structure, time granularity, and sampling pattern
4. a decision on whether you need time tables, space tables, spatio-temporal tables, or final training-sample export

Without a working database environment and raw data source, this repository cannot complete the full pipeline by itself.

## Why This Project Exists

The hard part of industrial time-series work is often not whether data exists, but whether that data can be turned into something stable and reusable for downstream systems.

- raw fields are inconsistent
- time granularity and sampling patterns are unstable
- temporal and spatial relationships are often mixed together
- training data usually requires another full round of restructuring

This project aims to transform raw industrial signals into structured assets that can be stored, analyzed, and used for model training.

## How To Use It

A typical workflow looks like this:

1. install and validate `TDengine` first
2. prepare raw industrial time-series data and field mappings
3. ingest the raw data into TDengine
4. construct time tables, space tables, and spatio-temporal tables as needed
5. perform cleaning, slicing, aggregation, and feature building on top of those tables
6. export the final results as JSON or SFT-ready samples for downstream model training

It is useful for:

- industrial data-governance projects
- equipment monitoring and fault-diagnosis tasks
- teams that need to convert raw time-series into training data
- systems that want to connect the database layer with the model-training layer

## How The Project Works

The current design can be understood as four major stages:

- ingestion
  - define TDengine schemas and persist raw data reliably
- structural organization
  - split raw data into time tables, space tables, or spatio-temporal tables
- feature processing
  - apply cleaning, slicing, aggregation, and context building
- sample export
  - turn structured outputs into training JSON or SFT-ready samples

In other words, this repository targets the middle layer between database engineering and model data engineering.

## What Needs To Be Configured

At minimum, you should define:

- TDengine connection information
  - such as host, port, database name, and access credentials
- raw field mappings
  - which fields represent time, tag, value, device identity, and so on
- table design
  - which time tables, space tables, or spatio-temporal tables are required
- export targets
  - whether the final output should be JSON, training samples, or intermediate feature artifacts

The key boundary is:

- this repository handles organization, feature construction, and sample export around TDengine
- `TDengine` itself still stores and queries the raw time-series data

So if the database layer is not ready, the governance workflow cannot be executed end-to-end.

## How It Helps Others

- helps industrial teams turn messy raw data into reusable data infrastructure
- helps ML teams reduce repeated manual cleaning and format conversion
- helps projects connect raw signals to model-training samples faster
- helps database-facing and model-facing teams collaborate through a clearer interface

## Source Origin

- derived from internal TDengine-based industrial data-governance prototypes
- representative scripts:
  - `insert_TDengine.py`
  - `TDengine_data_contron_use.py`
  - `2_insert_into_tdengine.py`
  - `3.insert_into_table.py`
  - `2024_10_24_formatted_data_control/`
  - `2024_9_29_Tdengine_Data_AutoFactor/`

## Good Technical Highlights

- engineering with TDengine in real industrial scenarios
- raw industrial time-series governance
- layered design with time, space, and spatio-temporal tables
- automatic training-sample generation

## One-Line Resume Version

Built a TDengine-based industrial data pipeline for ingestion, time slicing, spatio-temporal feature construction, and SFT data export, turning raw industrial time-series data into LLM fine-tuning samples.

## Remaining Cleanup Work

- remove repeated scripts and historical experiment folders
- anonymize database names, account info, and business-specific fields
- normalize module names and directory structure
- add a clear end-to-end data-flow document
- prepare sanitized sample data

## Recommended Initial Repo Structure

```text
tdengine-industrial-data-pipeline/
├── README.md
├── README_EN.md
├── LICENSE
├── requirements.txt
├── docs/
│   └── pipeline.md
├── pipeline/
│   ├── __init__.py
│   ├── tdengine_client.py
│   ├── ingest.py
│   ├── feature_builder.py
│   ├── spacetime_table.py
│   └── export_sft.py
└── examples/
    ├── sample_input.json
    └── run_pipeline.py
```

## Quick Start Idea

```bash
# 1. install and start TDengine
# 2. prepare raw industrial time-series data
# 3. define schemas and field mappings
# 4. then run the governance and export flow from this repository
```

## A More Accurate Mental Model

It is best to think about this project as:

- a data-organization and sample-building layer on top of `TDengine`
- not a replacement for the TDengine database itself

So the practical order is:

- get the database and raw data ready first
- then use this repository to connect data governance with training-sample generation
