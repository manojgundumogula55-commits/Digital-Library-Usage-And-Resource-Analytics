# Dataset

## Purpose
Store the raw and cleaned CSV files used by the project stages.

## Required files
- `library_usage_raw.csv` — original/raw project dataset used in Stage 1 and Stage 2.
- `library_usage_clean.csv` — cleaned dataset produced by Stage 2 and used by Stage 3 and Stage 4.

## Dataset information
The project uses a synthetic Digital Library Usage dataset for 2025, containing access records and the fields required for extraction, validation, cleaning and analysis.

| File | Rows | Columns |
|---|---|---|
| `library_usage_raw.csv` | 1,500 | 15 |
| `library_usage_clean.csv` | 1,456 | 19 |

The cleaned file has fewer rows because 29 duplicate records and 15 rows with unreadable dates were removed. It has four extra columns (`month`, `month_no`, `weekday`, `hour`) created from the access date.

### Columns in the raw dataset
| Column | Description |
|---|---|
| access_id | Unique access identifier (A00001 format) |
| user_id | Anonymised user identifier |
| user_type | Undergraduate, Postgraduate, Faculty or Researcher |
| department | CSE, ECE, Mechanical, Civil, Management or Sciences |
| resource_id | Resource identifier (R001 format) |
| resource_title | Title of the resource |
| resource_type | E-Book, Journal, Database, Video or Thesis |
| publisher | Publisher of the resource |
| publication_year | Year the resource was published |
| access_datetime | Date and time of the access |
| session_minutes | Time spent in the session |
| device | Mobile, Laptop or Campus PC |
| downloaded | 1 if the resource was downloaded, otherwise 0 |
| rating | User rating from 1 to 5, where given |
| access_mode | On-Campus or Remote |

> **Important:** Keep the original/raw dataset separate from the cleaned dataset. Missing values should not be automatically replaced with zero when they represent information that was not reported (for example, a rating the user did not give).

## Output
The raw dataset is preserved for reference, while the cleaned CSV provides the common input for the aggregation, analysis and visualization stages.
