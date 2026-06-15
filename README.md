# Snowflake ELT Pipeline with dbt and Airflow

## Architecture Diagram

![Architecture Diagram](https://github.com/ramineniadithyaghs/Snowflake-ELT-Pipeline-with-dbt-and-Airflow/blob/main/Images/Architecture_Adithya.png)

## Airflow DAG

![Airflow DAG](https://github.com/ramineniadithyaghs/Snowflake-ELT-Pipeline-with-dbt-and-Airflow/blob/main/Images/dbt_dag2.png)

## Data Flow Diagram

![DataFlowDiag](https://github.com/ramineniadithyaghs/Snowflake-ELT-Pipeline-with-dbt-and-Airflow/blob/main/Images/DataFlowDiagram.png)

A production-grade ELT (Extract, Load, Transform) data pipeline that processes millions of records using modern data stack best practices. This project demonstrates enterprise-scale data engineering with Snowflake, dbt, and Apache Airflow.
📊 Architecture Overview
Show Image
Pipeline Flow

Extract: Raw data from TPCH orders table (Snowflake sample database)
Load: Ingest into Snowflake data warehouse
Transform: dbt models create staging, intermediate, and mart layers
Orchestrate: Airflow DAGs automate the entire workflow
Test: Automated data quality checks ensure integrity


🎯 Key Features
✅ Modular dbt Project

Source definitions and documentation
Staging models for raw data cleaning
Intermediate models for business logic
Fact tables and data marts for analytics
Custom macros (e.g., discount price calculations)

✅ Comprehensive Testing

Generic tests (uniqueness, not_null, relationships)
Singular tests for business logic validation
Schema validation and data quality checks

✅ Production-Ready Orchestration

Airflow DAGs with retry logic
Task dependencies and error handling
Scheduled runs and monitoring

✅ Best Practices

Medallion architecture (Bronze → Silver → Gold)
DRY principles with dbt macros
Version control and CI/CD ready
Clear documentation and lineage


🛠️ Tech Stack
ComponentTechnologyPurposeData WarehouseSnowflakeStorage and computeTransformationdbt (Data Build Tool)SQL-based transformationsOrchestrationApache AirflowWorkflow automationLanguagePython 3.9+Scripting and automationVersion ControlGit/GitHubCode management
```
📁 Project Structure
snowflake-dbt-airflow-pipeline/
│
├── data_pipeline/           # Core dbt project
│   ├── models/             # dbt models (staging, marts)
│   ├── macros/             # Reusable SQL functions
│   ├── tests/              # Data quality tests
│   └── dbt_project.yml     # dbt configuration
│
├── dbt-dag/                # Airflow DAGs
│   └── dbt_pipeline.py     # Orchestration logic
│
├── Images/                 # Architecture diagrams
│   ├── Architecture_Adithya.png
│   ├── dbt_dag2.png
│   └── DataFlowDiagram.png
│
└── README.md              # This file
```
🚀 Getting Started
Prerequisites
```
Snowflake Account (free trial available)
Python 3.9+
dbt-snowflake (pip install dbt-snowflake)
Apache Airflow 2.0+
Git
```
Installation

Clone the repository

bashgit clone https://github.com/ramineniadithyaghs/snowflake-dbt-airflow-pipeline-adithyaghs.git
cd snowflake-dbt-airflow-pipeline-adithyaghs

Set up dbt profile

bash# Create ~/.dbt/profiles.yml
nano ~/.dbt/profiles.yml
Add your Snowflake credentials:
yamldata_pipeline:
  target: dev
  outputs:
    dev:
      type: snowflake
      account: YOUR_ACCOUNT
      user: YOUR_USERNAME
      password: YOUR_PASSWORD
      role: YOUR_ROLE
      database: YOUR_DATABASE
      warehouse: YOUR_WAREHOUSE
      schema: YOUR_SCHEMA
      threads: 4

Install dependencies

bashpip install dbt-snowflake apache-airflow

Test dbt connection

bashcd data_pipeline
dbt debug

Run dbt models

bashdbt run
dbt test

📊 Visualizations
Airflow DAG
Show Image
Orchestrated workflow showing task dependencies and execution flow
Data Flow
Show Image
End-to-end data transformation journey from source to analytics

🧪 Data Quality & Testing
This project includes comprehensive testing:
Generic Tests:

Uniqueness checks on primary keys
Not-null validation on required fields
Referential integrity between tables
Accepted value ranges

Singular Tests:

Custom business logic validation
Cross-model consistency checks
Revenue calculation accuracy

Run tests:
bashdbt test

📈 Key Transformations

Source Layer (sources.yml)

Defines raw TPCH orders table
Documents data lineage


Staging Layer (stg_orders.sql)

Cleans raw data
Standardizes column names
Applies data types


Intermediate Layer (int_orders_enhanced.sql)

Business logic calculations
Uses custom macros (discount pricing)
Aggregations and joins


Mart Layer (fct_orders.sql)

Analytics-ready fact table
Optimized for BI tool consumption
Pre-aggregated metrics

🔄 Airflow Orchestration
The pipeline is automated with Airflow:
DAG Features:

✅ Scheduled daily runs
✅ Automatic retries on failure
✅ Email alerts for errors
✅ Task dependencies ensure correct execution order
✅ SLA monitoring

Start Airflow:
bashairflow db init
airflow webserver --port 8080
airflow scheduler

💡 Use Cases
This pipeline architecture can be adapted for:

E-commerce Analytics - Order processing and customer insights
Financial Reporting - Transaction data transformation
Supply Chain - Inventory and logistics tracking
Marketing Analytics - Campaign performance measurement



🔮 Future Enhancements
 Add CI/CD pipeline with GitHub Actions
 Integrate with BI tools (Tableau/Power BI)
 
📝 License
This project is licensed under the MIT License - see the LICENSE file for details
👤 Author
Adithya Ramineni
LinkedIn: linkedin.com/in/adithyaramineni
Email: adithyachowdaryr@gmail.com
🙏 Acknowledgments
Snowflake for the TPCH sample database
dbt Labs for excellent documentation
Apache Airflow community for orchestration tools
📫 Contact
Have questions or want to collaborate? Feel free to reach out!
⭐ If you found this project helpful, please star this repository! ⭐

Built with ❤️ by a data engineer passionate about building reliable, scalable data infrastructure.
