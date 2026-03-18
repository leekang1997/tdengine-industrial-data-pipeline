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
