# Formula 1 Winners - Exploratory Data Analysis (EDA)

## Project Overview
This project performs a comprehensive Exploratory Data Analysis (EDA) on Formula 1 race winners dataset spanning from 1950 to 2024. The analysis includes data cleaning, statistical analysis, transformation, outlier detection, and visualization.

---

## Dataset Information
- **Dataset Name**: f1_winners.csv
- **Total Records**: 1,110 F1 race results
- **Time Period**: May 13, 1950 to May 5, 2024 (74 years)
- **Features**: 7 columns
  - Grand Prix (venue)
  - Date (race date)
  - Winner (driver name)
  - Car (constructor/team)
  - Laps (number of laps completed)
  - Time (race duration)
  - Name Code (driver code)

---

## Project Structure
```
.
├── f1_winners.csv                    # Original dataset
├── EDA_F1Winners.py                  # Complete Python analysis script
├── f1_winners_cleaned_final.csv      # Cleaned dataset
├── README.md                         # This file
└── Supporting CSV files:
    ├── top_10_winners.csv
    ├── top_10_grand_prix.csv
    ├── top_10_cars.csv
    ├── races_by_decade.csv
    ├── laps_distribution.csv
    └── year_laps_correlation.csv
```

---

## Analysis Steps Performed

### 1. **Dataset Overview**
- Examined dataset structure (1,110 rows × 7 columns)
- Identified 115 unique winners, 53 Grand Prix locations, 63 constructors
- Reviewed data types and basic statistics

### 2. **Data Quality Checks**
- Missing values: Only 0.27% (3 rows in Laps and Time columns)
- Duplicates: 0 duplicate entries found
- Formatting issues: 1,106 rows with extra spaces in Winner names
- No erroneous data (negative laps, etc.)

### 3. **Data Cleaning**
- Filled missing Laps values with median (65.0)
- Forward-filled missing Time values
- Stripped leading/trailing spaces from Winner column
- Converted Date column to datetime format
- Result: 100% clean dataset with zero missing values

### 4. **Descriptive Statistics**
**Laps Statistics:**
- Mean: 64.65, Median: 65.0, Mode: 53.0
- Standard Deviation: 20.24
- Skewness: 2.49 (highly right-skewed)
- Kurtosis: 16.85 (heavy tails indicating outliers)

**Top Winners:**
1. Lewis Hamilton - 103 wins (9.3% of all races)
2. Michael Schumacher - 91 wins
3. Max Verstappen - 58 wins

**Top Constructors:**
1. Ferrari - 245 wins (22.2%)
2. Mercedes - 116 wins (10.5%)

### 5. **Data Transformation & Encoding**
- Applied StandardScaler to normalize Laps column
- Log transformation to reduce skewness (2.49 → -2.14)
- Label encoded categorical variables (Winner, Grand Prix, Car)
- Created 5 new features for machine learning readiness

### 6. **Outlier Detection & Treatment**
**IQR Method:**
- Detected 65 outliers (5.86% of data)
- Bounds: [27, 99] laps
- Primary outliers: Indianapolis 500 races (200 laps)

**Z-Score Method:**
- 12 extreme outliers (Z-score > 3)
- Treated outliers using capping method

**Key Finding:** Indianapolis 500 races (1950-1960) are legitimate outliers with 200 laps vs typical 50-75 laps

### 7. **Data Visualization**
Created 7 comprehensive visualizations:
- Histogram: Laps distribution (right-skewed)
- Box plot: Outlier visualization
- Bar charts: Top winners, Grand Prix locations, constructors
- Scatter plot: Laps vs Year temporal analysis
- Line chart: Racing frequency by decade

### 8. **Key Insights & Interpretation**

**Winner Analysis:**
- Lewis Hamilton dominates with 103 wins (12 more than Schumacher)
- Top 3 drivers account for 252 wins (22.7% of all races)
- Average wins per driver: 9.65

**Constructor Dominance:**
- Ferrari leads with 246 wins, 32 ahead of Mercedes
- Ferrari has won 22.2% of all F1 races

**Temporal Trends:**
- Racing frequency increased 128% from 1950s (87 races) to 2010s (198 races)
- Modern era shows concentration of wins among fewer drivers

**Race Characteristics:**
- Most races have 50-75 laps (median: 65)
- High positive skewness due to Indianapolis 500 outliers
- Belgium 2021: Only 1 lap completed (rain suspension)

**Data Quality:**
- Excellent: 99.73% complete data
- No duplicates, minimal missing values
- All formatting issues resolved

---

## Technologies Used
- **Python 3.x**
- **Libraries:**
  - pandas (data manipulation)
  - numpy (numerical operations)
  - matplotlib (visualization)
  - seaborn (statistical visualization)
  - scipy (statistical analysis)
  - scikit-learn (preprocessing, encoding)

---

## How to Run

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

### In VS Code:
1. Install Python and Jupyter extensions in VS Code
2. Open `EDA_F1Winners.py`
3. Click "Run All Cells" or execute cell-by-cell
4. View interactive visualizations in the output panel

### In Jupyter Notebook:
```bash
# Convert to Jupyter notebook
jupyter nbconvert --to notebook EDA_F1Winners.py
# Or run directly
jupyter notebook EDA_F1Winners.ipynb
```

---

## Key Findings Summary

### 📊 Dataset
- 1,110 F1 races analyzed over 74 years
- 115 unique winners, 53 venues, 63 constructors
- 99.73% data completeness

### 🏆 Dominance
- **Driver:** Lewis Hamilton (103 wins)
- **Constructor:** Ferrari (245 wins)
- **Venue:** Great Britain (75 races)

### 📈 Trends
- 128% increase in racing frequency (1950s to 2010s)
- Lap counts standardized to 50-75 in modern era
- Concentration of wins among elite drivers

### ⚠️ Anomalies
- Indianapolis 500: 200 laps (legitimate outliers)
- Belgium 2021: 1 lap only (weather suspension)
- 65 outliers identified and documented

---

## Files Generated
1. `f1_winners_cleaned_final.csv` - Cleaned dataset
2. `top_10_winners.csv` - Top winners data
3. `top_10_grand_prix.csv` - Top venues data
4. `top_10_cars.csv` - Top constructors data
5. `races_by_decade.csv` - Temporal analysis
6. `laps_distribution.csv` - Lap frequency data
7. `year_laps_correlation.csv` - Temporal correlation data

---

## Implications for Modeling
- Dataset is clean and ML-ready
- Features scaled and encoded
- Outliers documented and treated
- Temporal features extracted
- Skewness addressed through transformation

---

## Author
[Your Name]  
Roll No: [Your Roll Number]  
Course: MSc Computer Science  
Date: October 21, 2025

---

## License
This project is for educational purposes.

---

## Acknowledgments
- Data source: Formula 1 historical race results
- Analysis period: 1950-2024
- Dataset includes all F1 World Championship races