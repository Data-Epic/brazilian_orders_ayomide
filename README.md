# Brazilian Customers Orders ETL Pipeline

The Brazilian E-Commerce Public Dataset by Olist is processed through an ETL (Extract, Transform, Load) pipeline in this project. Polars handles data processing, while DuckDB serves as the target database. For simplified deployment and scalability, the entire system—including data ingestion scripts, unit tests, and the DuckDB database—is containerized using Docker. The Docker environment is set up to extract the data and offer a command-line interface (CLI) for executing queries on the data using DuckDB.

## Features
Extracting data from various CSV files within the Olist dataset
Transforming and modeling data to construct dimensional and fact tables
Conducting sophisticated data analysis to produce informative aggregate tables
Importing processed data into a DuckDB database
Implementing extensive unit testing for data preprocessing and database functions
Containerizing the entire ETL pipeline using Docker to ensure reproducibility and ease of deployment

## Prerequisites

- Docker and Docker Compose
- Git

## Quick Start

1. Clone the repository:
git clone https://github.com/Data-Epic/customer_orders_pipeline_peter.git
cd customer_orders_analysis

2. Download the dataset:
- Get the list dataset and information from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce), unzip the downloaded zip file
- Create a `data/` Place all CSV files in the `data/` directory

3. Build and run the Docker container:
docker-compose up --build

This will:
Build the Docker image based on the provided Dockerfile.
Install necessary dependencies.
Download and unzip the DuckDB CLI.
Unzip the retail dataset.
Run the data ingestion script.
Open the DuckDB CLI.

4. In a new terminal, start the container:
docker start -ai customers-analysis-etl-duckdb-container

5. Query the loaded tables in DuckDB:
```sql
SELECT * FROM fact_table LIMIT 5;
SELECT * FROM top_selling_sellers LIMIT 5;
SELECT * FROM most_used_payment_type LIMIT 5;


Input Data

olist_customers_dataset.csv
olist_order_items_dataset.csv
olist_orders_dataset.csv
olist_products_dataset.csv


Output Tables
The pipeline generates the following analytical and aggregate tables in DuckDB:

fact_table
top_selling_sellers
top_selling_product_category
order_status_count
top_average_delivery_time
average_payment_value
loyal_customers
most_used_payment_type

Project Structure
customer_orders_analysis/
# Input CSV files
# Source code files
# Unit tests
# Docker configuration
# Docker Compose configuration
# Python dependencies
# This file



If you need to update or add dependencies and packages, modify the requirements.txt file and rebuild the Docker image using:

docker compose up --build

Data Ingestion:

Modify the data_ingestion.py script to change the data ingestion process according to your requirements.

Dependency Issues:
Ensure all required dependencies are listed in the requirements.txt file.