# Stage 2 — Data Extraction, Validation & Cleaning

## Purpose
Extract the information required for the project analysis, identify common data-quality issues, and apply only the necessary cleaning steps to prepare the dataset for later stages.

## Required checks
- Extract selected fields such as resource, resource type, user type, department and other required information.
- Identify resources used by multiple departments and accesses by faculty and researchers.
- Extract accesses with recorded downloads, accesses with ratings, and remote access cases.
- Check for missing values and calculate missing-value percentages.
- Check for duplicate records and duplicate Access IDs.
- Validate Access ID, User ID and Resource ID formats and access date values.
- Check for blank text values and unnecessary leading or trailing spaces.
- Validate categorical values, session time, ratings and download flags.
- Apply the required cleaning steps based on the validation results.
- Preserve missing values where the user did not report information (for example, ratings) instead of automatically replacing them with zero.

> **Important:** The original dataset is kept separate from the cleaned dataset. Cleaning is performed only where a data-quality issue is identified.

## Output
The stage produces the validated and cleaned dataset (`library_usage_cleaned.csv`) used by the aggregation, analysis and visualization stages of the project.
