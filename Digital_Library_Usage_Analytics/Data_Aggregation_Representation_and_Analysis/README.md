# Stage 3 — Data Aggregation, Representation & Analysis

## Purpose
Summarise the cleaned Digital Library Usage dataset into aggregation tables, arrange the results as cross-tabulations and pivot tables, and answer the project's analysis questions.

## Required checks
- Load the cleaned dataset (`library_usage_cleaned.csv`) produced by Stage 2.
- Build an overall usage summary: total accesses, unique users, average session, download rate, average rating and remote access share.
- Aggregate usage by resource, resource type and publisher.
- Aggregate usage by department and user type.
- Aggregate usage by month, weekday and hour.
- Aggregate usage by device and access mode.
- Represent the results as cross-tabulations and pivot tables: department vs resource type, user type vs resource type, month vs resource type, weekday vs hour, device vs access mode, and average session by department and resource type.
- Answer the analysis questions: most-used resources and resource types, underused resources, most active departments and user types, peak months, weekdays and hours, session time and downloads, remote vs on-campus usage, and highest-rated resources.
- Summarise the key findings in one table.

> **Important:** All counts, percentages and rankings are calculated from the loaded data and are not hard-coded. Missing ratings are left out of rating averages, not treated as zero. Underused resources are defined as the lowest 10% of access counts.

## Output
The stage produces aggregated summary tables and key findings (`resource_summary.csv`, `department_summary.csv`, `monthly_summary.csv`, `weekday_hour_matrix.csv`, `key_findings.csv`) used by the visualization and interpretation stage.
