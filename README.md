# Arsenal FC AWS ETL Pipeline

**End-to-end modern data pipeline** built on AWS to process Arsenal FC match results, player statistics, and performance metrics.

This project demonstrates legacy ETL modernisation patterns (similar to SAS Data Integration Studio batch workflows) using current cloud-native tools.

### Project Goals
- Ingest raw football data
- Clean, transform and enrich the data
- Load into a queryable data warehouse
- Add basic orchestration and data quality checks
- Showcase skills transferable from 20+ years of SAS ETL experience

### Architecture
![Architecture Diagram](architecture.png)   <!-- You can add a simple diagram later -->

**Tech Stack**
- **AWS**: S3, Glue (ETL), Athena, Step Functions / EventBridge
- **Languages**: Python (PySpark), SQL
- **Others**: Pandas (local exploration), Git

### Data Sources
- Historical Arsenal match results and league tables from football-data.co.uk
- Player statistics from public Kaggle datasets

### Key Features
- Raw data landing zone in S3
- Automated Glue jobs for transformation (data cleaning, goal difference, win rate, etc.)
- Partitioned data by season
- SQL views for common analytics (e.g., Arsenal performance under different managers)
- Data quality validation

### Insights You Can Get
```sql
-- Arsenal's win rate by manager
SELECT manager, COUNT(*) as matches, SUM(win) as wins, 
       ROUND(SUM(win)*100.0/COUNT(*), 2) as win_rate
FROM arsenal_performance 
GROUP BY manager;# arsenal-fc-aws-etl-pipeline
End-to-end AWS ETL pipeline for Arsenal FC match and performance data — SAS legacy modernisation example
