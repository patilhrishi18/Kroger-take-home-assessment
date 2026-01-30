
# Kroger Take Home Assessment  
**Space to Sales: Produce Table Optimization (5 New Tables)**

## Overview
This repository contains an end-to-end data analytics solution for a Kroger produce merchandising optimization case study.

The business problem: A Kroger store is introducing **five new produce tables** and wants to determine **which produce items should be placed on each table** to maximize sales performance while respecting **physical space constraints** and minimizing waste risk.

The solution combines data cleaning, exploratory analysis, ranking logic, and space-constrained allocation to generate actionable table layout recommendations.

---

## Business Objective

**Goal:**  
Maximize sales impact from new produce tables by prioritizing high-performing items while ensuring table capacity constraints are respected.

**Key Constraints:**
- Fixed table capacity (physical footprint)
- Produce items vary in width and space usage
- Sales performance differs by item and commodity

**Key Questions Answered:**
- Which produce items deserve priority placement?
- How should items be distributed across 5 tables?
- How efficiently is space being utilized?

---

## Data Sources

### 1. Produce Table Sales Dataset
Contains performance-related fields:
- Base UPC  
- Pct Sales (%)  
- Sales Score (performance quartile)  
- Commodity and table metadata  

File:
- `produce_table.csv`

### 2. Produce Item Information Dataset
Contains physical product attributes:
- UPC Description  
- Commodity  
- Item Width (inches)  

File:
- `produce_info.csv`

### 3. Processed Dataset
Merged dataset used for analysis and allocation logic:

File:
- `produce_sales_info_merged.csv`

---

## Project Workflow

### Step 1: Data Cleaning & Preparation
- Loaded raw datasets
- Validated schema and keys
- Handled missing values
- Merged datasets using Base UPC
- Standardized column formats

### Step 2: Exploratory Data Analysis (EDA)
Insights extracted:
- Identified top-performing produce categories
- Analyzed footprint distribution
- Evaluated sales contribution by commodity
- Flagged high-demand and high-space items

### Step 3: Ranking Logic (Sales vs Space Efficiency)
A composite ranking metric was created using:
- Recent sales contribution (%)
- Sales score
- Item width (space penalty)

This ensures priority is given to items that:
- Generate strong sales impact
- Use shelf space efficiently
- Balance performance and footprint

### Step 4: Table Allocation Algorithm

Each table capacity:
- Length = 14 feet  
- Converted capacity = **168 inches per table**

Allocation logic:
- Sort produce items by ranking score
- Assign items to the first available table with sufficient remaining space
- Track remaining capacity per table
- Prevent table overflow

This ensures operational feasibility and merchandising clarity.

---

## Outputs

### Jupyter Notebook (Primary Analysis)
File:
- `Kroger_Assessment.ipynb`

Includes:
- Data processing
- Visualization
- Ranking methodology
- Allocation logic
- Final table layouts

---

### Business Report
File:
- `Kroger_Assessment - Space to Sales.docx`

Includes:
- Executive summary
- Business interpretation
- Recommendations
- Key assumptions

---

### Presentation Deck
File:
- `Kroger Take Home Assessment Insights PPT.pptx`

Includes:
- Stakeholder-ready visuals
- Final recommendations
- Business storytelling

---

## Repository Structure

Recommended structure:

```
.
├── README.md
├── notebooks/
│   └── Kroger_Assessment.ipynb
├── data/
│   ├── raw/
│   │   ├── produce_table.csv
│   │   └── produce_info.csv
│   └── processed/
│       └── produce_sales_info_merged.csv
├── reports/
│   ├── Kroger_Assessment - Space to Sales.docx
│   └── Kroger Take Home Assessment Insights PPT.pptx
├── requirements.txt
└── .gitignore
```

---

## How To Run This Project

### Local Setup

1. Clone repository
```
git clone <repository-url>
cd <repository-folder>
```

2. Create virtual environment
```
python -m venv .venv
source .venv/bin/activate   # Mac/Linux
.venv\Scripts\activate      # Windows
```

3. Install dependencies
```
pip install -r requirements.txt
```

4. Launch notebook
```
jupyter notebook
```

Open:
```
notebooks/Kroger_Assessment.ipynb
```

---

## Requirements

Suggested `requirements.txt`:

```
pandas
numpy
matplotlib
seaborn
jupyter
notebook
```

---

## Assumptions

- Sales Score reflects relative item performance tiers
- Pct Sales represents recent demand trends
- Width in inches is the primary space constraint
- Greedy allocation provides a practical and explainable solution
- Shrink risk is indirectly inferred due to lack of direct shrink data

---

## Limitations

- No direct shrink or waste dataset provided
- Greedy allocation is not globally optimal
- Seasonality effects not modeled
- Store-level demand variation not included

---

## Future Improvements

If extended into production:

- Introduce optimization models (ILP / knapsack)
- Add shrink risk weighting
- Add seasonal adjustment factors
- Build automated ETL pipeline
- Deploy dashboard for merchandising teams

---

## Author

**Hrishikesh Anil Patil**  
Data Analytics Engineer  
LinkedIn: https://linkedin.com/in/patilhrishikesh18  
GitHub: https://github.com/<your-username>

---
