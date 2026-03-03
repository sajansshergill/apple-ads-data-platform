# 🍎 Privacy-First Apple Ads Data Platform

## 📌 Overview
This project simulates a web-scale, privacy-aware advertising data platform inspoired by Apple Ads Data Products Engineering.

It processes high-volume and events (impressions, clicks, installs, revenue) using a moder data stack:
- Kafka (Streaming ingestion)
- Spark Structures Streaming (Distributed processing)
- Apache Iceberg (ACID Lakehouse tables)
- Airflow (Orchestration)
- SQL / Trino (Analytics layer)
- Python (Feature engineering & monitoring)
- Docker (Local clusetr simulation)

The system is designed to support:
- Algorithm & ML teams
- Product & Data Insights
- Sales & Marketing
- Executive reporting

All with privacy-first architecture principles.

## 🏗️ Architecture
                 +---------------------+
                 |  Event Generator    |
                 |  (10M+ ad events)   |
                 +----------+----------+
                            |
                            v
                    +----------------+
                    |    Kafka       |
                    | (Streaming)    |
                    +--------+-------+
                             |
                             v
               +--------------------------+
               | Spark Structured Streaming|
               | (Dedup, Enrich, Validate)|
               +------------+-------------+
                            |
                            v
                 +----------------------+
                 |  Apache Iceberg     |
                 |  (ACID Lakehouse)   |
                 +----------+----------+
                            |
          +----------------+----------------+
          |                                 |
          v                                 v
   Feature Store                     Analytics Layer
   (CTR, CVR, eCPM)                  (SQL / Trino)
          |                                 |
          v                                 v
     ML Workloads                    Executive Dashboards

## 🎯 Objectives
This project demonstrates the ability to:
- Build resilient streaming pipelines at scale
- Design partitioned Iceberg lakehouse tables
- Implement privacy-aware data modeling
- Develop ML=ready feature engineering layers
- Automate workflows using Airflow
- Monitor reliability and data quality
- Simulate produciton-grade data services

## 🛠️ Tech Stack
| Layer         | Technology                         |
| ------------- | ---------------------------------- |
| Streaming     | Kafka                              |
| Processing    | Spark Structured Streaming         |
| Storage       | Apache Iceberg                     |
| Query         | Spark SQL / Trino                  |
| Orchestration | Airflow                            |
| Monitoring    | Python logging + custom checks     |
| DevOps        | Docker + CI/CD                     |
| Security      | SHA-256 hashing, role-based access |


## 📦 Repository Structure
<img width="290" height="542" alt="image" src="https://github.com/user-attachments/assets/0c479dde-db3e-4658-868a-0da58b89bd62" />

## 📊 Data Model
### Fact Tables
- fact_impressions
- fact_clicks
- fact_installs
- fact_revenue

Partitioned by:
- event_date
- campaign_id

### Dimension Tables
- dim_campaign
- dim_advertiser
- dim_device
- dim_geo

## 🔐 Privacy-First Design
This platform enforces:
- SHA-256 hashing for device identifiers
- No raw PII storage
- Partition-level access simulation
- Encryption-at-rest (simulated)
- Aggregation thresholds to prevent re-identification

Privacy principles are embedded at ingestion.

## ⚡ Feature Engineering Layer
Derived metrics:
- CTR (Click Through Rate)
- CVR (Coversion Rate)
- eCPM
- Revenue per campaign
- Rolling 7-day performance
- Engagement decay scores

Output table:
feature_store_campaign_daily

This enables downstream:
- Bidding algorithms
- Budget optimization models
- Anomaly detection
- Campaign performance forecasting

## 🔁 Orchestration (Airflow)
DAGs included:
- streaming_job_monitor
- nightly_aggregation
- feature_recompute
- data_quality_validation

Supports:
- Retry logic
- SLA monitoring
- Failure alerts

## 📈 Monitoring & Reliability


