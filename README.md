# chux-effective-doodle



**Use Case**: A retail company wants to analyze customer behavior on their e-commerce platform to improve sales and customer experience.

### **1. Solution Description**:

**Problem**: The retail company has disparate data sources (website logs, transaction databases, customer reviews, etc.) and lack a unified view of customer behavior, server activity, and search. This makes it challenging to derive actionable insights.

**Solution**: A cloud-native data pipeline that ingests data from various sources, processes it, and stores it in a unified data warehouse. This data is then used for analytics derive insights.

### **2. Architectural Design**:

**Data Ingestion**:
Data ingestion — Data is received from data sources to either a Landing Zone (LZ) or introduced into a streaming pipeline.

**Data Orchestration**:
- **Process Raw Data**:  Using AWS Step Functions and AWS MWAA to pick up data from the "Raw Zone" and move into the pipline for processing
- **Real-time Processing**: AWS Kenisis AWS MKS for real-time data which is inventory data in this use case. Inventory must be real-time so fulfilment and replenishment
                            can be achieved.

**Data Processing (ETL)**:
- **AWS Glue Streaming**: Uses AWS Glue streaming to process (ETL) data comming in from MKS and Kenisis.
- **AWS Glue Jobs**: Schedule ETL Jobs.
- **AWS Glue Databrew**: A data preparation tool that makes it easier for data analysts and data scientists to clean and normalize data.
- **AWS Glue Catalog**: Stores metadata related to data sources, data transformations, and resulting data sets. This includes table definitions,
                        job definitions, and other related metadata. Provides "crawlers" that can infer data schemas from ODBC, JDBC, S3 data sources.

**Exception and Error Handling**:
- **Monitoring**: Prometheus and Grafana for monitoring the health of the pipeline.
- **Alerting**: PagerDuty for real-time alerts on failures.
- **Data Quality Checks**: Great Expectations for ensuring data quality.

### **3. Stakeholders and Challenges**:

**Stakeholders**:
- **Data Engineers**: Concerned about the scalability and maintainability of the solution.
- **Data Scientists**: Interested in the quality and accessibility of data for analytics.
- **Business Analysts**: Need timely and accurate reports.
- **IT Security**: Concerned about data privacy and security.

**Challenges**:
- **Data Quality**: Ensuring consistent and high-quality data was a challenge given the disparate sources.
- **Scalability**: The solution needed to handle increasing data volumes as the company grew.
- **Security**: Ensuring GDPR compliance and data encryption.

### **4. Lessons Learned**:

- **Iterative Development**: Start small and expand. Initially, focus on critical data sources and then expand to others.
- **Data Quality**: Invest in data quality from the start. It's easier to maintain quality than to fix issues later.
- **Feedback Loop**: Regularly gather feedback from stakeholders to ensure the solution meets their needs.

### **5. Technical Capabilities**:

- **Data Ingestion**: Real-time and batch data ingestion capabilities.
- **Data Storage**: Scalable storage solutions for both raw and processed data.
- **Data Processing**: Batch and real-time data processing capabilities.
- **Data Delivery**: Tools for both visualization and advanced analytics.

