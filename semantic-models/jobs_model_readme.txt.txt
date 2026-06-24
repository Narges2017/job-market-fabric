# Semantic Model: jobs model

## Overview
- **Model Name**: jobs model
- **Workspace**: job_market
- **Last Updated**: 23/06/2026
- **Purpose**: Job market analysis (jobs, applications, companies, locations, dates)

## Tables Included
- dim_date
- dim_jobs
- dim_location
- dim_company
- fact_table

## Key Relationships (from Model View)
- dim_date → fact_table (date_id)
- dim_jobs → fact_table (job_id)
- dim_location → fact_table (location_id)
- dim_company → fact_table (company_id)

## Important Measures in fact_table
- avg_salary
- max_salary  
- min_salary


## Notes
- This is a star schema model (Fact + Dimension tables)
- Fact table contains salary and job application metrics

## Screenshots
Location: docs/semantic-model-screenshots/
- relationships.png
- tables_list.png