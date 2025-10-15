# Cytotoxicity Analysis - In VitroDB v4.3 (AUG 2024)

## Overview

This project analyzes cytotoxicity screening data from the **In VitroDB v4.3 database (August 2024)**, containing over 10,000 chemical compounds tested for in-vitro cytotoxic effects. The analysis aims to identify patterns in chemical toxicity and communicate findings in a clear, accessible way for both technical and non-expert audiences.

## Dataset

- **Source**: In VitroDB v4.3 (AUG 2024)
- **Size**: ~10,000+ chemical compounds
- **Format**: Excel (.xlsx)
- **Key Metrics**:
  - `cytotox_median_um`: Median cytotoxicity concentration in micromolar (µM) - **lower values indicate MORE toxicity**
  - `nhit`: Number of positive hits (measurable toxic effects)
  - `ntested`: Number of assays conducted
  - Various bounds and log-transformed values

## Project Structure

```
axeleres-assignment/
├── cytotoxicity_analysis.ipynb          # Main analysis notebook
├── cytotox_invitrodb_v4_3_AUG2024.xlsx # Raw dataset
├── README.md                            # This file
└── Images/                              # Generated visualizations
    ├── distribution_analysis.png
    ├── correlation_matrix.png
    ├── toxicity_categories.png
    ├── top_20_toxic_chemicals.png
    └── testing_coverage_analysis.png
```

## Approach

### 1. Data Familiarization & Quality Check
- Loaded and examined dataset structure
- Identified key columns and their meanings
- Checked for missing values, duplicates, and outliers
- Calculated basic statistics: unique chemicals, testing coverage, hit rates

### 2. Trend Exploration
- Analyzed distributions of cytotoxicity metrics (both linear and log scales)
- Identified top 10 most toxic (lowest µM) and least toxic (highest µM) chemicals
- Explored relationships between:
  - Number of tests vs number of hits
  - Hit ratio vs cytotoxicity levels
  - Testing coverage vs reliability of measurements

### 3. Visualization & Communication
Created three main visualizations with detailed captions:
- **Distribution by Toxicity Categories**: Classified chemicals into 4 toxicity levels
- **Top 20 Most Toxic Chemicals**: Ranked by potency (lowest µM values)
- **Testing Coverage Analysis**: Relationship between testing thoroughness and reliability

### 4. Summary & Reflection
Synthesized key findings and highlighted surprising observations about:
- Chemical toxicity patterns
- Testing reliability
- Real-world implications for safety assessment

## Key Findings

### Chemical Toxicity Distribution
- **~85-90%** of tested chemicals showed measurable cytotoxic effects
- Most chemicals fall into the **"moderately toxic" range (10-100 µM)**
- Toxicity values span **several orders of magnitude** (thousands-fold difference between most and least toxic)

### Testing Insights
- Chemicals tested more extensively (>100 assays) showed **more reliable toxicity estimates**
- Hit consistency (nhit) and toxicity potency (µM concentration) are **distinct characteristics**
- Average hit rate correlates with testing coverage, emphasizing need for comprehensive protocols

### Most Toxic Chemicals
- Identified **top 20 most cytotoxic compounds** requiring very low concentrations (<10 µM) to induce effects
- Many recognized industrial chemicals and pharmaceuticals, validating dataset reliability
- Clear distinction between highly toxic and moderately toxic chemicals

## Visualizations

### 1. Distribution by Toxicity Category
![Toxicity Categories](distribution_analysis.png)

**Insight**: The majority of chemicals cluster in the moderate toxicity range, with relatively few showing extreme toxicity. This suggests most tested compounds require careful but not exceptional handling protocols.

### 2. Top 20 Most Toxic Chemicals
![Top 20 Toxic](top_20_toxic_chemicals.png)

**Insight**: The most toxic chemicals show tight clustering in their potency values, indicating a distinct group of highly hazardous compounds that warrant prioritized risk assessment.

### 3. Testing Coverage and Reliability
![Testing Coverage](testing_coverage_analysis.png)

**Insight**: More extensively tested chemicals have tighter confidence bounds and more stable toxicity estimates, emphasizing the importance of comprehensive testing for accurate safety assessments.

## How to Run the Analysis

### Prerequisites
Ensure you have Python 3.7+ installed with the following libraries:
```bash
pip install pandas numpy matplotlib seaborn scipy openpyxl jupyter
```

### Running the Notebook
1. Clone or download this repository
2. Ensure the dataset file `cytotox_invitrodb_v4_3_AUG2024.xlsx` is in the same directory
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook cytotoxicity_analysis.ipynb
   ```
4. Run all cells sequentially (Cell → Run All)

### Expected Output
- Statistical summaries printed to console
- 5 visualization plots saved as PNG files
- Complete analysis with interpretations in the notebook

## Dependencies

```
pandas >= 1.3.0
numpy >= 1.21.0
matplotlib >= 3.4.0
seaborn >= 0.11.0
scipy >= 1.7.0
openpyxl >= 3.0.0  # For reading Excel files
jupyter >= 1.0.0
```

## Interpretation Guide

### Understanding Cytotoxicity Values
- **Lower µM = MORE toxic**: A chemical with 1 µM is more toxic than one with 100 µM
- **Highly Toxic**: < 10 µM
- **Moderately Toxic**: 10-100 µM
- **Mildly Toxic**: 100-1000 µM
- **Low Toxicity**: > 1000 µM

### Understanding Testing Metrics
- **nhit**: Number of positive results - higher indicates more consistent toxicity
- **ntested**: Total tests conducted - higher indicates more thorough evaluation
- **hit_ratio**: Consistency of toxic effects (nhit/ntested)

## Key Takeaways for Discussion

1. **Data Quality**: Dataset is comprehensive with minimal missing values and good coverage across compounds

2. **Toxicity Patterns**: Clear distribution patterns emerge, with most chemicals showing moderate toxicity rather than extremes

3. **Testing Importance**: More extensive testing yields more reliable results, highlighting the value of thorough screening protocols

4. **Risk Assessment**: The identification of highly toxic chemicals provides actionable insights for prioritizing safety measures

5. **Statistical Approach**: Log-transformed values provide better distribution for statistical analysis, though raw µM values are more interpretable for non-experts

## Questions for Follow-up Discussion

- How should regulatory thresholds be set based on these distributions?
- What factors explain the wide range of toxicity values?
- How can we improve testing protocols based on coverage analysis?
- What are the implications for chemical safety in industrial settings?

## Author Notes

This analysis balances technical rigor with accessibility, aiming to make complex toxicology data understandable without sacrificing accuracy. The visualizations and narrative structure are designed for presentation to diverse audiences, from regulatory experts to general stakeholders.

---

**Analysis Date**: October 2024
**Dataset Version**: In VitroDB v4.3 (AUG 2024)
**Tool**: Jupyter Notebook with Python 3
