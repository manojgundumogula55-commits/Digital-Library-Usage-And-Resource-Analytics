# Stage 1 — Data Loading & Reading

## Purpose
Load the Digital Library Usage dataset and understand its basic structure before further extraction, validation, cleaning and analysis.

## Required checks
- Load the `library_usage_raw.csv` dataset using Pandas.
- Display the complete dataset for an initial view.
- Display the first five and last five records.
- Check the number of rows and columns.
- Display the column names.
- Check the data types of all columns.
- Inspect the dataset information using `df.info()`.
- Generate basic descriptive statistics.
- Explore important categorical fields such as resource type, user type, department, device and access mode.
- Select the columns required for the project analysis.
- Filter cases by resource type, user type, department, device and access mode.
- Identify records containing rating, session time and download information.

> **Important:** The notebook uses the actual dataset loaded from the CSV file. The row and column counts are obtained from the loaded data rather than being hard-coded.

## Output
The stage produces an initial understanding of the dataset, basic category distributions and filtered subsets that can be used by the following project stages.
