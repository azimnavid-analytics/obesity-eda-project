# obesity-eda-project
Explored obesity data (2,100+ records) via EDA. Key finding: weight not height drives classification; BMI cleanly separates all seven classes. Family history &amp; diet align with obesity as expected, but snacking behavior ran backwards worth a second look. Python, pandas, seaborn. 📊
# Obesity Level Prediction: Exploratory Data Analysis

Exploratory data analysis of a dataset on obesity levels, examining how eating habits, physical condition, and lifestyle factors relate to obesity classification.

## Dataset

The dataset (`ObesityDataSet_raw_and_data_sinthetic.csv`) contains 2,100 records with 17 features covering:

- **Demographics:** Age, Gender, Height, Weight
- **Eating habits:** frequency of vegetable consumption (FCVC), number of main meals (NCP), eating between meals (CAEC), high-calorie food consumption (FAVC), water intake (CH2O)
- **Lifestyle:** physical activity frequency (FAF), time using technology devices (TUE), alcohol consumption (CALC), smoking (SMOKE), calorie monitoring (SCC), mode of transportation (MTRANS)
- **Family history:** family history with overweight
- **Target variable:** `NObeyesdad` : obesity level classified into 7 categories (Insufficient Weight, Normal Weight, Overweight Level I/II, Obesity Type I/II/III)

## Tools Used

- Python, pandas, numpy
- matplotlib, seaborn

## Approach

1. Initial inspection:  shape, data types, missing values, memory usage, summary statistics
2. Target class distribution
3. Univariate analysis of numeric features (histograms) and categorical features (count plots)
4. Outlier detection via boxplots (Age, Height, Weight)
5. Bivariate analysis: Weight/Height by obesity class, categorical features vs. obesity class (100% stacked bar charts)
6. Correlation heatmap across numeric features (checked for multicollinearity ahead of future modeling)
7. Engineered BMI (Weight / Height²) and examined its spread across obesity classes

## Key Findings

- **Weight, not height, drives classification.** Weight varies sharply and monotonically across obesity classes, while height shows almost no separation between classes, weight is doing nearly all the work in determining the class label.
- **BMI cleanly separates the classes.** As expected given it's derived from weight and height, BMI shows a clear, well-ordered progression across all 7 obesity categories with far less overlap than either raw feature alone.
- **Family history and diet habits track with obesity.** Family history of overweight and frequent high-calorie food consumption both line up clearly with higher obesity classes; calorie monitoring and active transportation (walking/biking vs. car) show a similar pattern.
- **Weak linear correlations among numeric features overall** the strongest pair is Height–Weight (r = 0.46), and nothing approaches problematic multicollinearity (>0.7–0.8) for future modeling.
- **Data skews young:** most individuals are 20–25 years old, eat 3 meals a day, and report low physical activity.
- **One counter-intuitive result:** the relationship between snacking (CAEC) and obesity class ran opposite to expectation and is flagged as needing a closer look a good candidate for follow-up analysis rather than a settled conclusion.

## Repository Structure

```
├── Notebook/
│   └── obesity_eda.ipynb
├── Data/
│   └── ObesityDataSet_raw_and_data_sinthetic.csv
├── EDA_Charts/
│   ├── 01_Target_Class_Distribution.png
│   ├── 02_Numeric_Feature_Histograms.png
│   ├── 03_Categorical_Feature_Counts.png
│   ├── 04_Outlier_Boxplots_Age_Height_Weight.png
│   ├── 05_Weight_Height_by_Obesity_Class.png
│   ├── 06_Categorical_Features_vs_Obesity_Class.png
│   ├── 07_Correlation_Heatmap.png
│   └── 08_BMI_by_Obesity_Class.png
└── README.md
```

## How to Run

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Notebook/obesity_eda.ipynb
```

## Next Steps

- Investigate the counter-intuitive snacking (CAEC) vs. obesity class relationship
- Build a classification model (e.g., Random Forest, XGBoost) to predict `NObeyesdad`
- Feature engineering beyond BMI (e.g., interaction terms between lifestyle features)
