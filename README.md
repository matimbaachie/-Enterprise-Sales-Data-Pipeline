# Enterprise Sales Data Pipeline

##  Project Summary

This project delivers a robust, scalable data pipeline that ingests, transforms, and analyzes enterprise sales data across multiple regions. Built on Azure Data Factory, Azure SQL Database, and Synapse Analytics, it powers executive dashboards and machine learning models for revenue forecasting.

Sales data arrives daily from CRM exports, point-of-sale terminals, and third-party APIs. The system orchestrates ETL across structured and semi-structured sources, applies business rules, and outputs a unified data model for business stakeholders.

---

##  Key Features

- Scheduled ingestion from APIs, Blob Storage, and CRM exports
- Data cleansing and joins with ADF data flows
- Metadata tagging and data lineage tracking
- Business logic in SQL-based transformations
- Synapse views and Power BI dashboards for sales KPIs
- Key Vault, RBAC, and private endpoints for secure operations

---

##  Technologies Used

| Purpose             | Technology                        |
|---------------------|------------------------------------|
| Orchestration       | Azure Data Factory                 |
| Storage             | Azure Blob Storage, Data Lake Gen2 |
| Processing          | Azure Data Flows, SQL Stored Procs |
| Warehousing         | Azure Synapse Analytics            |
| Scripting           | Python (for API fetch + blob move) |
| Dashboarding        | Power BI                           |
| Security            | Azure Key Vault, Managed Identity  |
| Deployment          | ARM Templates + Azure CLI          |

---

##  How I Delivered It

1. **Data Ingestion**
   - Used ADF Copy activities to pull from:
     - CRM SFTP exports (CSV)
     - POS API (JSON via REST)
     - Vendor-provided FTP (XML files)
   - Metadata-driven pipeline architecture using config table in SQL

2. **Data Transformation**
   - Built ADF mapping data flows to:
     - Normalize formats (e.g. currency, date-time)
     - Remove duplicates, nulls, junk values
     - Join customer & product dimension tables

3. **Python Scripts**
   - Azure Function in Python:
     - Authenticates with POS API using OAuth2
     - Downloads ZIP file and extracts to staging blob
   - Used in ADF Web Activity for event-driven runs

4. **Data Warehouse Layer**
   - Stored transformed data in star-schema in Synapse DW
   - Created views and stored procs for:
     - Sales margin trends
     - Regional performance YoY
     - Product category breakdown

5. **Dashboarding & Security**
   - Published curated data into Power BI workspace
   - Enforced RBAC and role separation (Admin, DataOps, BI)
   - All secrets managed via Key Vault-linked integration runtimes

---


---

## Outcomes

-  Fully automated ingestion from 3 independent sources
-  Reduced daily manual reporting from 6 hrs → 15 minutes
-  Enabled self-service BI across sales & finance teams
-  End-to-end secured deployment with Key Vault and private networks
-  Reduced data errors and duplicate rows by 95%

---




