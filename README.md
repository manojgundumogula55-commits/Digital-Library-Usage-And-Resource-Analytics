# Digital Library Usage and Resource Analytics

## Project Overview

This project analyzes access records of a digital library (e-books, journals, databases, videos and theses) for the year 2025 using Python and Pandas. The analysis follows a step-by-step data-analysis workflow covering data loading, extraction, validation, cleaning, aggregation, analysis, visualization, and interpretation.

**Team:** Team 17  
**Course:** Data Analysis Essentials (DAE)  
**Dataset:** Digital Library Usage Records (2025)

---

## Problem Statement

Digital libraries spend a large part of their budget on licences for e-books, journals and databases. Without usage analysis, it is hard to know which resources are used, who uses them, and when demand is highest. Some resources may be heavily used while others are rarely opened, and information such as ratings or session times is sometimes missing from the records.

The project uses a reproducible data-analysis process to study usage patterns across resources, departments, user types, time periods and devices, so that the library can plan its collection, licences and support.

---

## Objectives

- Study digital library usage across the months of 2025.
- Identify the most used resources and resource types.
- Compare usage across departments and user types.
- Find peak months, weekdays and hours of access.
- Examine session length, downloads and ratings separately.
- Compare remote and on-campus access, and usage by device.
- Identify underused resources that may need a licence review.
- Clean and standardize the dataset before aggregation and visualization.
- Present findings using tables, statistical summaries, and charts.

---

## Scope and Significance

### Scope

The project is limited to the access records in the supplied dataset. It covers accesses from January to December 2025 and focuses on resource details, user and department information, access time, device, access mode, session length, downloads and ratings.

### Significance

The analysis gives a structured way to understand how a digital library is used. It organizes information that is difficult to compare across resources, departments and time periods, and supports decisions on licence renewal, staffing and system capacity. The results are intended for data-analysis and educational purposes and should not be read as the usage of any real library.

---

## Dataset

### Source

The project uses a **synthetic Digital Library Usage dataset** generated with Python for this project. Data-quality problems (missing values, duplicates, invalid dates and sessions, inconsistent text) were added on purpose so that the validation and cleaning stages have real issues to find.

> Replace this section if you use a real dataset (for example, a library usage export or a Kaggle dataset), and update the numbers in the sections below.

### Dataset Description

The raw project dataset contains:

- **1,500 records (accesses)**
- **15 columns (fields)**
- Date range: **January–December 2025**
- Resource types: **E-Book, Journal, Database, Video, Thesis**
- User types: **Undergraduate, Postgraduate, Faculty, Researcher**

Important attributes include:

- `access_id` — unique access identifier (A00001 format)
- `user_id` — anonymised user identifier
- `user_type` — Undergraduate, Postgraduate, Faculty or Researcher
- `department` — CSE, ECE, Mechanical, Civil, Management or Sciences
- `resource_id` — resource identifier (R001 format)
- `resource_title` — title of the resource
- `resource_type` — E-Book, Journal, Database, Video or Thesis
- `publisher` — publisher of the resource
- `publication_year` — year the resource was published
- `access_datetime` — date and time of the access
- `session_minutes` — time spent in the session
- `device` — Mobile, Laptop or Campus PC
- `downloaded` — 1 if the resource was downloaded, otherwise 0
- `rating` — user rating from 1 to 5, where given
- `access_mode` — On-Campus or Remote

### Data Quality in the Raw Data

The raw data does not have complete information for every access:

- Rating is missing for **89 of 1,500** accesses.
- Session time is missing for **67** accesses, and **39** more have invalid values (zero, negative, or longer than 8 hours).
- Device is missing for **21** accesses and publisher for **16**.
- **15** accesses have unreadable dates.
- **29** records are duplicates.

Missing ratings are kept as missing and are **not treated as zero**, because the user may simply not have rated the resource.

---

## Project Workflow

The repository follows four practical stages:

1. **Data Loading & Reading**
2. **Data Extraction, Validation & Cleaning**
3. **Data Aggregation, Representation & Analysis**
4. **Data Visualization, Results & Interpretation**

The stages correspond to the larger data-analysis workflow used for the project.

---

## Repository Structure

```text
Digital-Library-Usage-Analytics/
│
├── 01_Data_Loading_and_Reading/
│   ├── README.md
│   └── Data_Loading_and_Reading.ipynb
│
├── 02_Data_Extraction_Validation_and_Cleaning/
│   ├── README.md
│   └── Data_Extraction_Validation_Cleaning.ipynb
│
├── 03_Data_Aggregation_Representation_and_Analysis/
│   ├── README.md
│   └── Data_Aggregation_Analysis.ipynb
│
├── 04_Data_Visualization_Results_and_Interpretation/
│   ├── README.md
│   └── Data_Visualization_Results_Interpretation.ipynb
│
├── Presentation/
│   ├── DAE Review 1.pptx
│   └── DAE Review 2.pptx
│
├── data/
│   ├── library_usage_raw.csv
│   └── library_usage_clean.csv
│
├── output/
│   └── figures/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Data Processing and Analysis

### Data Loading and Inspection

Stage 1 loads the dataset and performs basic inspection, including:

- first and last records
- dataset dimensions
- column names
- data types
- dataset information
- descriptive statistics
- categorical-value exploration
- basic filtering of records

### Missing Values and Duplicate Checks

Stage 2 checks for:

- missing values
- missing-value percentages
- duplicate records
- duplicate Access IDs
- invalid Access, User and Resource ID formats
- invalid dates
- dates outside the expected range
- invalid categories, sessions, ratings and download flags
- blank text values
- leading/trailing whitespace

### Data Cleaning and Filtering

The cleaning stage applies only the transformations supported by the validation results:

- removing duplicate records
- standardizing text (for example `FACULTY` to `Faculty`, ` cse ` to `CSE`)
- converting `access_datetime` to a datetime type and removing rows whose date cannot be read
- setting invalid session times to missing and filling them with the median of the same resource type
- keeping missing ratings as missing
- filling missing publisher and device with `Unknown`
- creating `month`, `month_no`, `weekday` and `hour` columns
- performing final validation after cleaning

The raw dataset is preserved separately from the cleaned dataset. After cleaning, the dataset has **1,456 rows and 19 columns**.

### Aggregation and Analysis

Stage 3 uses Pandas operations such as:

- `groupby()`
- `agg()`
- `pivot_table()` and `crosstab()`
- `value_counts()`
- `sort_values()`
- filtering
- date feature extraction (month, weekday, hour)
- comparisons across resources, resource types, departments, user types, time periods, devices and access modes

The analysis also examines session length, download rate and ratings, and identifies underused resources (the lowest 10% by access count).

### Visualization

Stage 4 produces charts for:

- accesses by month
- top 10 most accessed resources
- accesses by department and by user type
- share of accesses by resource type
- peak usage by weekday and hour
- average session length by user type
- download rate by resource type
- device and access mode
- rating distribution
- monthly usage by resource type

The charts are stored in `output/figures/`.

---

## Findings

The current dataset shows that:

- **April** (182 accesses), **October** (181) and **March** (169) are the busiest months, and **June** is the quietest (52). About **42%** of accesses happen between 4 PM and 10 PM, with the busiest hour at 4 PM.
- **E-Books** are the most used resource type (**36.5%** of accesses), followed by Databases (26.6%) and Journals (26.2%).
- The **top 10 resources** account for **47.1%** of all accesses, led by `R070`. **9 resources** fall in the lowest 10% of usage and are candidates for licence review.
- **CSE** is the most active department (286 accesses) and **Civil** the least active (213).
- **Undergraduates** make **53.6%** of accesses, followed by Postgraduates (25.3%), Faculty (12.0%) and Researchers (9.2%).
- The average session is **29.6 minutes**, and about **33.2%** of accesses end in a download. Videos have the highest download rate (43.8%), but they are only 2.2% of all accesses, so this figure rests on a small number of records.
- **40.7%** of accesses are remote, and Laptop is the most used device.
- The average rating is **3.77 out of 5**, based on the 1,367 accesses that have a rating.

The project should be read as an analysis of **the access records in this dataset**, not as a measurement of any real library.

---

## Underused Resource Note

For the licence-review analysis, a resource is treated as **underused** when its access count falls in the lowest 10% of all resources that were accessed. This is an **operational definition for this project**, not a library standard. A low count does not by itself mean a resource is unnecessary, because some resources are specialised or newly added.

---

## Limitations

- The dataset is synthetic, so the patterns reflect how it was generated and not real user behaviour.
- The data covers one year (2025) and cannot show long-term trends.
- Missing ratings were kept as missing, so rating results describe only users who chose to rate.
- Missing and invalid session times were filled with the median of the same resource type, which slightly reduces variation in session length.
- Rows with unreadable dates were removed, so counts exclude them.
- Some categories, such as Video, have few records, so percentages for them are less reliable.
- Associations in the data should not be presented as proof of causation.

---

## How to Run the Project

### Requirements

Python 3 with the packages listed in `requirements.txt`.

Install the required packages using:

```bash
pip install -r requirements.txt
```

### Running in Google Colab

1. Open the required `.ipynb` notebook in Google Colab.
2. Run the cells from top to bottom.
3. When a notebook asks for a CSV file, upload the appropriate dataset from the `data/` folder:
   - Stages 1 and 2: `library_usage_raw.csv`
   - Stages 3 and 4: `library_usage_clean.csv`
4. Start with Stage 1 and continue through Stage 4.
5. Stage 2 produces the cleaned dataset used by the later analysis stages.

### Recommended Order

```text
Stage 1 → Stage 2 → Stage 3 → Stage 4
```

---

## Team Information

**Team Number:** 17

| Team Member | Roll Number | Contribution |
|---|---|---|
| G.Sashank | 25B11AI316 | Data Loading, Reading & Filtering |
| G.Spandhana | 25B11AI340 | Data Extraction, Validation & Cleaning |
| B.Harika | 25B11AI527 | Data Aggregation, Representation & Analysis |
| V.Pavithra | 25B11AI520 | Data Visualization, Results & Interpretation |
| G.Manoj | 25B11AI385 | Dataset Preparation, Documentation, GitHub Repository & Review Presentations |

---

## Review Presentations

The Review-1 and Review-2 presentation files are included in the `Presentation/` folder as required for project documentation.

---

## Tools and Technologies

- **Python 3**
- **Pandas** — data loading, filtering, cleaning, grouping, aggregation and transformation
- **NumPy** — numerical calculations
- **Matplotlib and Seaborn** — data visualization
- **Google Colab / Jupyter Notebook** — notebook execution

---

## Conclusion

This project provides a structured analysis of digital library usage using a reproducible Python-based workflow. The analysis covers data quality checks, cleaning, aggregation, descriptive analysis, visualization, and interpretation while keeping the limitations of the source data visible throughout the process.
