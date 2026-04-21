# Hidden Value in Irish Retail
A CSO-based analysis of retail category trends in Ireland using Python

## Project Overview
This project explores retail category performance in Ireland using the **CSO Retail Sales Index (RSM08)** dataset. The goal was not just to compare raw category averages, but to identify which retail segments showed the strongest **hidden value** when performance, momentum, and volatility were considered together. [CSO RSM08](https://data.cso.ie/table/RSM08)

The project was designed as a portfolio case study to show how public economic data can be turned into a business-focused analytics story. Instead of building a generic dashboard, I created a simple scoring framework to highlight categories that looked strong beyond surface-level averages.

## Business Question
Which Irish retail categories show the strongest hidden value when we combine:
- Average retail index performance
- Month-over-month momentum
- Volatility or consistency over time

## Dataset
**Source:** Central Statistics Office (CSO) Ireland  
**Dataset:** Retail Sales Index (RSM08)  
**Link:** [https://data.cso.ie/table/RSM08](https://data.cso.ie/table/RSM08)

### Original dataset structure
The downloaded CSV contained:
- 10,912 rows
- 5 columns:
  - `Statistic Label`
  - `Month`
  - `NACE Group`
  - `UNIT`
  - `VALUE`

It also contained multiple retail measures in one file, including:
- Retail Sales Index Volume Adjusted
- Retail Sales Index Volume Adjusted Percentage Change over 1 month
- Retail Sales Index Volume Adjusted Percentage Change over 12 months
- Retail Sales Index Volume Unadjusted
- Retail Sales Index Value Adjusted
- Retail Sales Index Value Adjusted Percentage Change over 1 month
- Retail Sales Index Value Adjusted Percentage Change over 12 months
- Retail Sales Index Value Unadjusted

## Project Objective
The main objective of this project was to identify which retail categories in Ireland showed the strongest combination of:
1. Strong average performance
2. Positive monthly momentum
3. Manageable volatility

This was done by building a **Hidden Value Score** to rank retail categories using official CSO data from January 2021 to February 2026.

## Tools Used
- **Python**
- **Pandas**
- **Matplotlib**
- **Seaborn**
- **Google Colab**
- **GitHub**

## Data Cleaning
The original CSO file contained multiple retail measures in one CSV, so the first step was to isolate the most useful series for this analysis.

### Cleaning steps
- Uploaded the CSV into Google Colab
- Loaded the data into pandas
- Filtered the dataset to keep only:
  - `Retail Sales Index Volume Adjusted`
- Renamed columns for easier analysis:
  - `Statistic Label` → `statistic_label`
  - `Month` → `month`
  - `NACE Group` → `nace_group`
  - `UNIT` → `unit`
  - `VALUE` → `value`
- Converted the `month` column into a proper datetime format
- Removed rows with missing values in `value`
- Filtered the analysis to 14 final retail categories
- Calculated month-over-month percentage change for each category

## Final Analysis Dataset
After cleaning and filtering, the final working dataset contained:
- **868 rows**
- **14 retail categories**
- **Date range:** January 2021 to February 2026

### Overall numeric summary
- **Average retail index value:** 107.51
- **Median retail index value:** 106.0
- **Minimum value:** 26.0
- **Maximum value:** 141.7
- **Average month-over-month change:** 1.11%
- **Median month-over-month change:** 0.09%
- **Average volatility:** 8.89

## Methodology
The project was built in four stages:

### 1. Category comparison
I first created a summary table showing:
- Average value
- Minimum value
- Maximum value
- Number of observations

This gave a high-level view of category performance over time.

### 2. Trend analysis
I then visualized selected categories over time to compare how different parts of Irish retail behaved between 2021 and 2026.

### 3. Volatility analysis
For each category, I calculated month-over-month percentage changes and used the standard deviation of those changes as a measure of volatility.

### 4. Hidden Value Score
I built a custom score using:
- Average index value
- Average month-over-month change
- Volatility

Each metric was normalized using min-max scaling, and the final score was calculated as:

**Hidden Value Score =**
- 45% average value
- 35% average momentum
- 20% inverse volatility

This means categories were rewarded for:
- Higher average performance
- Stronger monthly momentum
- Lower volatility

## Key Findings

### Top hidden-value categories
The highest-ranked categories were:

1. **Retail sale of textiles, clothing and footwear** — Hidden Value Score: **80.00**
2. **Retail sale of books, newspapers and stationery** — Hidden Value Score: **69.48**
3. **Other retail sales** — Hidden Value Score: **68.28**
4. **Retail sale of books, newspapers, stationery and other goods** — Hidden Value Score: **67.37**
5. **Retail sale of furniture and lighting** — Hidden Value Score: **58.65**

### Main insights
- **Textiles, clothing and footwear** ranked highest because it combined strong average performance and strong monthly momentum, although it was also the most volatile category.
- **Books/newspapers/stationery** and **other retail sales** also scored strongly, suggesting that some less obvious categories outperformed expectations.
- **Food-related categories** were among the most stable, but they ranked lower in the hidden-value score because their momentum was weaker.
- The results show that stability alone does not produce a high hidden-value ranking; momentum and average performance matter too.

## Visuals
This project included:
- A category summary table
- An average retail index bar chart
- A multi-category trend chart
- Top monthly increases and decreases
- A volatility table
- A hidden value score table
- A final ranking chart of top hidden-value categories

<img width="1202" height="790" alt="image" src="https://github.com/user-attachments/assets/5546d1f0-98a7-48a5-97f4-245b81e809d6" />

<img width="1374" height="790" alt="image" src="https://github.com/user-attachments/assets/3f268204-38e3-4de6-b7a3-b05eaf7d9721" />

<img width="1222" height="790" alt="image" src="https://github.com/user-attachments/assets/faf7ecbb-2194-43be-ba26-e259c3e6f966" />


## Folder Structure
A clean structure for this repository could look like this:

```bash
hidden-value-irish-retail/
│
├── data/
│   ├── raw/
│   │   └── RSM08.20260420T110448.csv
│   └── processed/
│       ├── retail_cleaned_with_mom.csv
│       └── retail_hidden_value_score.csv
│
├── notebooks/
│   └── hidden_value_irish_retail.ipynb
│
├── images/
│   ├── average-retail-index.png
│   ├── retail-trends.png
│   └── top-hidden-value-categories.png
│
└── README.md
```

## How to Reproduce
1. Download the CSV from the official CSO dataset:
   - [https://data.cso.ie/table/RSM08](https://data.cso.ie/table/RSM08)
2. Upload the file into Google Colab
3. Run the notebook cells for:
   - Data loading
   - Cleaning
   - Category filtering
   - Trend analysis
   - Volatility calculation
   - Hidden value score creation
4. Save the cleaned outputs and charts

## Why this project matters
Retail data is often summarized at a high level, but category-level analysis can reveal very different patterns across consumer segments. This project shows how public economic data can be used to build a more decision-oriented retail story.

It also demonstrates practical analytics skills such as:
- Data cleaning
- Time-series analysis
- Custom metric design
- Visualization
- Business storytelling

## Limitations
- The analysis uses retail index data rather than direct revenue or profit data.
- The Hidden Value Score is a simplified ranking model and depends on the chosen weights.
- Some categories can appear strong because of momentum even if they are more volatile.
- This is a category-level national analysis, not a retailer-level commercial dataset.

If you'd like to connect, feel free to reach out on LinkedIn.
