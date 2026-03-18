# TDengine-Industrial-Data-Pipeline

[中文](./README.md) | [English](./README_EN.md)

`TDengine-Industrial-Data-Pipeline` 是一个面向工业时序场景的数据工程工具链，覆盖 TDengine 建表、数据写入、时序切分、时空表构建以及训练数据导出。

## 项目定位

工业时序数据往往存在这些特点：

- 数据源杂乱
- 字段不统一
- 时间粒度复杂
- 需要同时保留时间特征和空间特征
- 最终还要服务下游模型训练和诊断任务

这个项目的目标，是把“原始工业数据 -> TDengine -> 特征表 -> SFT 训练数据”的链路系统化。

## 当前能力

- TDengine 表结构创建
- 工业数据写入 TDengine
- 时间表、空间表与时空表构建
- 特征加工和序列切分
- 导出 JSON / SFT 训练数据

## 对应源码原型

- 工业 TDengine 数据治理与训练样本生成原型
- 关键脚本：
  - `insert_TDengine.py`
  - `TDengine_data_contron_use.py`
  - `2_insert_into_tdengine.py`
  - `3.insert_into_table.py`
  - `2024_10_24_formatted_data_control/`
  - `2024_9_29_Tdengine_Data_AutoFactor/`

## 适合展示的技术点

- TDengine 时序数据库工程化使用
- 原始工业时序数据治理
- 时间表、空间表、时空表三层结构设计
- 训练样本自动生成

## 适合写进简历的一句话

基于 TDengine 构建工业时序数据清洗与训练样本生成工具链，覆盖入库、时间切片、时空特征构建和 SFT 数据导出，打通原始工业数据到大模型微调语料的自动化流程。

## 当前需要清洗的内容

- 清理历史试验目录与重复脚本
- 去掉真实数据库名、账号和业务字段
- 统一模块命名与目录结构
- 补一份整体数据流说明图
- 添加脱敏样例数据

## 推荐的仓库初始结构

```text
tdengine-industrial-data-pipeline/
├── README.md
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
