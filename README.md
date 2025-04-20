# Customer Account Data Pipeline

## Overview

This project implements a robust data pipeline for processing and analyzing customer account data using Azure services. The pipeline extracts data from on-premises storage, performs data cleaning and transformation, and applies Slowly Changing Dimensions (SCD) techniques before storing the data in an Azure SQL Database. The architecture supports Bronze, Silver, and Gold layer processing for scalable and accurate analytics.

### Key Features

- Data ingestion from on-prem file system to Azure Data Lake Storage (ADLS) Gen2 (Bronze Layer)
- Data transformation and deduplication (Silver Layer)
- SCD Type 1 and Type 2 operations for various datasets (Gold Layer)
- Final data loading into Azure SQL Database

## Setup Steps

1. **Install Self-hosted Integration Runtime**  
   Install and register Microsoft Integration Runtime on your local system for data movement.

2. **Configure ADLS Gen2 and Containers**  
   - Create ADLS Gen2 storage account and define folder hierarchy: Bronze, Silver, and Gold.
   - Set up containers and folders to hold data at each processing stage.

3. **Create Linked Services in Azure Data Factory (ADF)**  
   - Local File System (using Integration Runtime)
   - ADLS Gen2
   - Azure SQL Database
   - Azure Key Vault for managing secrets

4. **Pipeline Creation**  
   - **Pipeline 1 (Bronze):** Copy on-prem files to ADLS Bronze folder using `ForEach` and `Copy` activity.
   - **Pipeline 2 (Silver):** Remove duplicates via Data Flow using `groupBy()` and `first()` functions.
   - **Pipeline 3 (Gold):** Apply SCD Type 1 or Type 2 via Data Flows for:
     - Accounts, Transactions, Customers (SCD Type 1)
     - Loans, Loan Payments (SCD Type 2)

5. **Azure SQL Table Setup**  
   - Create required SQL tables with metadata columns (`created_by`, `created_date`, `updated_by`, `updated_date`, `isActive`).

## Contributors

- Deepthi KanamataReddy








