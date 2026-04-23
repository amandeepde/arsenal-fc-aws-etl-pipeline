# Arsenal FC AWS ETL Pipeline

**End-to-end modern data pipeline** built on AWS to process Arsenal FC match results, player statistics, and performance metrics.

This project demonstrates legacy ETL modernisation patterns (similar to SAS Data Integration Studio batch workflows) using current cloud-native tools.

### Project Goals
- Ingest raw football data
- Clean, transform and enrich the data
- Load into a queryable data warehouse
- Add basic orchestration and data quality checks
- Showcase skills transferable from 20+ years of SAS ETL experience

### Tech Stack
- **AWS**: S3, Glue (ETL), Athena, Step Functions / EventBridge
- **Languages**: Python (PySpark), SQL
- **Others**: Pandas (for local exploration)

### Architecture
*(Diagram to be added soon)*

### Data Sources
- Historical Premier League & Arsenal match data from football-data.co.uk
- Player statistics from public Kaggle datasets

### Project Status

| Status | Phase                          | Details                                      |
|--------|--------------------------------|----------------------------------------------|
| ✅     | Data Exploration & Design      | Completed                                    |
| ✅     | Raw Data Collection            | Completed - Downloaded Premier League CSVs   |
| 🔄     | AWS Pipeline Development       | In Progress - Glue Jobs + PySpark            |
| 🔄     | Data Warehouse & Query Layer   | Planned - Athena views                       |
| 🔄     | Orchestration & Automation     | Planned - Step Functions                     |
| 📋     | Documentation & Demo           | In Progress                                  |

**Last Updated:** April 2026

### Key Features (Planned / In Progress)
- Raw data landing zone in S3 (bronze layer)
- Automated Glue jobs for data cleaning and transformation
- Season-based partitioning
- Data quality validation
- SQL views for analytics (e.g., Arsenal win rates by manager, goal trends, etc.)

### Sample Analytics
```sql
-- Arsenal's performance trends
SELECT 
    season,
    COUNT(*) as matches,
    SUM(CASE WHEN result = 'W' THEN 1 ELSE 0 END) as wins,
    ROUND(AVG(goals_scored), 2) as avg_goals_scored
FROM arsenal_matches
GROUP BY season
ORDER BY season DESC;
