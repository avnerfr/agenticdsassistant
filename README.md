# Agentic Exploratory Data Science Assistant

This AI based Python project provides a suggested assistant to data scientists who want to assess a new data set
with a simple UI, data scientists can laverage the power of LLMs and tools to quickly analyze and review new datasets

## Problem:
In real data science projects, a lot of time goes into data exploration, cleaning, feature engineering, and reporting this is a repetitive process, but crucial.

## Suggested Assistant:
This Agentic AI solution, provides a aet of worker agents where each agent is specialized in it's own task. agents can be added and removed as needed. an Orchestrator agent is responsible for the pipeline. A simple Gradio UI assit in loading the data and vieing the analytics.

## Architecture (Orchestrator–Worker)
I ued the Orchestrator–Worker pattern where an Orchestrator Agent (Project Manager) reads the prompt and the data 
**Input:** dataset (CSV, SQL table, Parquet, etc.)
**Decides workflow:** profiling → cleaning → feature engineering → modeling → reporting.
Coordinates worker outputs and keeps track of progress.

### Worker Agents:
**Data Profiling Agent**
Generates summary statistics, distributions, and correlations.
Detects missing values, anomalies, skewness.
Can use pandas-profiling or ydata-profiling.

**Data Cleaning Agent**
Suggests or applies imputation, normalization, outlier handling.
Documents cleaning decisions.
Feature Engineering Agent
Suggests new features (aggregations, encodings, transformations).
Uses domain knowledge if provided in prompt/context.

**Modeling Agent**
Runs quick baseline models (e.g., XGBoost, Logistic Regression).
Evaluates with cross-validation.
Reports best performing approach.
Report Generation Agent
Assembles profiling results, cleaning logs, and model performance.
Outputs Markdown/HTML/PDF report for stakeholders.

### Example Use Case
You drop in a new dataset (e.g., customer churn, credit scoring, IoT sensor logs).
Orchestrator → assigns profiling
Profiling Agent → finds 20% missing values in income
Orchestrator → sends task to Cleaning Agent
Cleaning Agent → imputes missing income using median per segment
Orchestrator → moves to Feature Engineering → Modeling → Report
End result: automated EDA + modeling pipeline with documented steps.

🚀 Why this helps your work
Saves hours of repetitive EDA per dataset.
Provides consistent documentation (huge for enterprise governance).
Can plug into Snowflake / Databricks to work on large datasets directly.
Extensible: you can swap in a Worker with a new model/technique as you experiment.


