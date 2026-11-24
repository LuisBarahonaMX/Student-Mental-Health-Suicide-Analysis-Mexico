# Student Mental Health, Depression and Suicide Trends in Mexico

### Exploratory Data Analysis, Geospatial Visualization, Statistical Forecasting, and Machine Learning with Python

<div align="center">

<img src="./depresion.jpg" alt="Student Mental Health and Depression Research in Mexico" width="650">

*Exploring mental health indicators, youth suicide trends, and student well-being through Data Science and responsible statistical analysis.*

</div>

**Project Type:** Academic Research and Public Health Data Analytics  
**Field:** Data Science | Mental Health Analytics | Machine Learning | Statistical Analysis | Geospatial Data  
**Programming Language:** Python  
**Environment:** Google Colab | Jupyter Notebook  
**Study Context:** Mexico and Universidad del Caribe, Quintana Roo  
**Author:** Data Engineer Luis Barahona

---

## 1. Project Overview

This research project explores mental health indicators, depression-related data, youth suicide mortality trends, and university student well-being in Mexico.

The project combines two Jupyter notebooks with supporting spreadsheets, historical datasets, reference documents, and a research presentation.

Its objective is to investigate patterns in population-level mental health data and explore how statistical techniques and machine learning can support educational research.

The analysis covers:

- Historical mental health indicators.
- Depression-related rates by sex and state.
- Youth suicide mortality trends in Mexico.
- Regional comparisons.
- Geographic data visualization.
- Exponential smoothing forecasts.
- University student survey analysis.
- Educational withdrawal-related responses.
- Professional help-seeking responses.
- Exploratory classification models.

This repository presents an educational research workflow rather than a clinically validated mental health assessment or suicide prediction system.

---

## 2. Research Objectives

The project aims to:

1. Explore historical mental health indicators in Mexico.
2. Analyze depression-related rates by sex and geographic region.
3. Examine youth suicide mortality trends from 1998 to 2023.
4. Identify historical periods with relatively high recorded rates.
5. Visualize state-level patterns using geographic information.
6. Apply exploratory statistical forecasting methods.
7. Analyze university student responses about emotional well-being.
8. Explore associations involving academic pressure, financial difficulties, and family support.
9. Test machine learning models on selected survey responses.
10. Examine the limitations and ethical requirements of mental health analytics.

---

## 3. Repository Components

The project includes two complementary notebooks.

### Notebook 1 — Student Depression and Suicide Analysis in Mexico

**Original file:**

`LB_DATOS_DEPRESION_Y_SUICIDIO_ESTUDIANTIL_MEXICO.ipynb`

This notebook contains the main experimental workflow.

It includes:

- Mental health data preparation.
- Descriptive statistical analysis.
- Correlation visualizations.
- K-Means clustering.
- Decision Tree regression.
- Geographic analysis with GeoPandas.
- Exponential smoothing.
- Youth suicide trend analysis.
- University student survey analysis.
- Exploratory classification models.

### Notebook 2 — Mental Health Disorders Analysis

**Original file:**

`Analisis_Trastornos_Mentales.ipynb`

This notebook focuses on descriptive analysis of mental health disorder indicators.

Its main sections examine:

- National depression trends.
- Comparisons between male and female records.
- States with high recorded depression-related rates.
- Comparisons between selected disorder categories.
- Regional differences.
- Identification of high-rate years.

The notebook expects a previously prepared Excel dataset.

---

## 4. Research Data

The project uses multiple datasets addressing different populations and outcomes.

These datasets should not be combined into a single statistical population without verifying their definitions and compatibility.

### 4.1 Mental Health Indicators

**File:** `Mental_05.xlsx`

The notebook uses this file to examine selected mental and behavioral disorder indicators.

The analyses include depression and anorexia/bulimia categories.

The main operations involve filtering records, restructuring tables, comparing sex-specific rates, and exploring changes over time.

### 4.2 Cleaned Mental Health Dataset

**File:** `mental_salud_limpio.xlsx`

This prepared dataset supports the second notebook.

Its analytical structure includes:

- Federal entity.
- Disorder category.
- Annual rates.
- National and state-level observations.

### 4.3 Youth Suicide Mortality

**File:** `1998-2023_tasas_mortalidad_porentidad.xlsx`

This dataset is used to examine recorded mortality rates associated with intentional self-inflicted injuries among people aged 10–29 years.

The notebook analyzes:

- National trends.
- State-level differences.
- Selected regional averages.
- Historical years with high recorded mortality rates.

These statistics describe an age group, not specifically people enrolled in educational institutions.

### 4.4 University Student Survey

The project also explores a questionnaire associated with Universidad del Caribe.

**Study context:** Student emotional well-being and educational experiences.

The survey contains questions about:

- Age.
- Employment while studying.
- Educational motivation.
- Academic evaluation pressure.
- Family support.
- Financial difficulties.
- Emotional experiences.
- Thoughts of leaving university.
- Professional psychological support.

The survey is described as a sample of approximately 100 students.

Saved notebook outputs include 102 valid age observations, while some questionnaire items have fewer responses.

The sample should not be interpreted as representative of every student at Universidad del Caribe.

### 4.5 Geographic Data

**File:** `Shapefile - Estados.zip`

The notebook uses this geographic dataset to visualize state-level indicators on a map of Mexico.

### 4.6 Supporting Research Documents

The project materials also include:

- EAP_Suicidio23.pdf
- 07-Panorama-Trastornos-Mentales.pdf
- Academic documents concerning student depression.
- Additional mortality-related data files.

These resources provide supporting documentation and research context.

---

## 5. Data Preparation

The notebooks use Pandas to import and transform Excel datasets.

### Example

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_excel(
    "Mental_05.xlsx",
    skiprows=5
)
```

The preprocessing workflow includes:

- Examining data structures.
- Selecting relevant rows.
- Filtering national records.
- Converting rates into numerical values.
- Restructuring annual tables.
- Encoding categorical variables.
- Handling missing observations.
- Creating derived fields.
- Preparing datasets for statistical analysis.

Some sections use manually specified column positions and names that depend on the original Excel layout.

Consequently, changes to the source spreadsheets may require updates to the preprocessing code.

---

## 6. Mental Health Indicators in Mexico

The main notebook explores selected depression and eating-disorder indicators.

The analysis examines national records and comparisons by sex.

### Exploratory Methods

The notebook includes:

- Descriptive statistics.
- Correlation heatmaps.
- Annual comparisons.
- K-Means clustering.
- Decision Tree regression.

### K-Means Clustering

K-Means is used to explore groups within selected observations.

The notebook standardizes numerical variables using StandardScaler.

```python
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_scaled = scaler.fit_transform(
    df_tasas[["Año", "Sexo", "Tasa"]]
)

kmeans = KMeans(
    n_clusters=3,
    random_state=42
)
```

The experiment investigates similarities among observations.

The resulting clusters do not establish clinically defined groups or mental health diagnoses.

---

## 7. Decision Tree Regression

The first notebook applies DecisionTreeRegressor to estimate selected mental health rates from encoded variables.

### Model

```python
from sklearn.tree import DecisionTreeRegressor

model = DecisionTreeRegressor(
    max_depth=4,
    random_state=42
)
```

### Saved Experimental Results

| Metric | Value |
|:---|---:|
| R² | 0.9956 |
| MSE | 9.0553 |

These figures come from the notebook's saved execution.

### Interpretation

Although the recorded R² is high, it should not be interpreted as proof that the model reliably forecasts mental health conditions.

The dataset is small, and the experiment uses a random train-test split.

The model is an educational regression exercise and has not undergone independent external or temporal validation.

---

## 8. Geographic Analysis

The notebook uses GeoPandas to explore the geographic distribution of selected mental health indicators.

### Tools

- GeoPandas.
- Matplotlib.
- State shapefiles.
- Pandas.

### Workflow

1. Upload the Excel data.
2. Upload the state shapefile archive.
3. Extract the geographic files.
4. Load the shapefile.
5. Match state names with analytical data.
6. Merge geographic and statistical records.
7. Visualize the results.

### Example

```python
import geopandas as gpd

mapa = gpd.read_file(
    "path/to/states.shp"
)

mapa.plot(
    column="Tasa",
    cmap="OrRd",
    legend=True,
    edgecolor="black"
)
```

The resulting geographic visualization supports exploratory comparisons between states.

Geographic differences should not automatically be interpreted as differences in underlying prevalence without considering reporting coverage and denominator definitions.

---

## 9. Exponential Smoothing Forecasting

The notebook explores future mental health indicator values using Statsmodels.

### Model

```python
from statsmodels.tsa.holtwinters import (
    ExponentialSmoothing
)

model = ExponentialSmoothing(
    series,
    trend="add",
    seasonal=None
)

fitted = model.fit()
forecast = fitted.forecast(3)
```

This configuration models an additive trend without seasonality.

### Saved Demonstration

The notebook includes example three-step forecasts for depression and anorexia/bulimia indicators.

### Limitations

The saved execution contains warnings about an unsupported time index.

The forecast output uses a numerical index rather than verified future calendar-year labels.

There is also no independent temporal forecasting accuracy assessment.

Therefore, these results should be interpreted as methodological demonstrations, not validated epidemiological forecasts.

---

## 10. Youth Suicide Mortality Analysis

The project examines mortality rates associated with intentional self-inflicted injuries among young people aged 10–29 years in Mexico.

### Historical Coverage

**1998–2023**

### Analytical Procedures

- National mortality-rate trend.
- Time series by selected state.
- Regional trend comparisons.
- Ranking historical years by national mortality rate.
- Visualization of long-term changes.

### Selected Saved Result

The recorded national rate for 2023 is:

**8.3952**

The precise unit and denominator should be confirmed from the original source documentation before the result is used outside this research context.

### Important Distinction

The original mortality series covers people aged 10–29.

It does not identify whether each person was attending school or university.

Accordingly, it should be described as youth suicide mortality rather than exclusively student suicide mortality.

---

## 11. University Student Survey Analysis

The main notebook includes an exploratory analysis of student questionnaire responses associated with Universidad del Caribe.

The survey examines topics such as:

- Family support.
- Work and study responsibilities.
- Financial difficulties.
- Academic pressure.
- Emotional well-being.
- Thoughts about leaving university.
- Professional help-seeking.

### Age Distribution

The saved descriptive output reports:

| Statistic | Value |
|:---|---:|
| Nonmissing age observations | 102 |
| Mean age | 21.55 |
| Median age | 21 |
| Minimum age | 18 |
| Maximum age | 37 |

### Data Quality Observation

The notebook's calculated `Puntuación` variable contains only zeros in the saved descriptive table.

Therefore, the notebook does not establish a valid numerical depression severity score.

No clinical diagnosis should be inferred from this variable.

### Privacy Considerations

Questionnaire responses may contain sensitive mental health information.

The repository should not publish raw participant-level survey data, email addresses, timestamps, or other potentially identifying information without documented authorization and appropriate privacy safeguards.

---

## 12. Student Survey Machine Learning

The notebook explores several classification algorithms using selected questionnaire features.

### Input Features

The models use variables related to:

- Age.
- Employment status.
- Family support.
- Financial difficulties.
- Emotional experiences.
- Academic evaluation pressure.

Categorical variables are transformed into numerical labels.

### Algorithms

The notebook evaluates:

1. Support Vector Machine (SVM).
2. Multinomial Naive Bayes.
3. Decision Tree Classifier.
4. Random Forest Classifier.

The classification targets are derived from self-reported survey answers.

They are not medically validated outcomes.

---

## 13. Classification Results

### Support Vector Machine

**Task:** Classify whether students reported thoughts related to leaving university.

The model uses a linear SVM.

### Saved Results

| Metric | Value |
|:---|---:|
| Test observations | 21 |
| Accuracy | 61.9% |
| Positive-class precision | 0.67 |
| Positive-class recall | 0.86 |
| Positive-class F1-score | 0.75 |

The evaluation uses a small holdout set.

The positive class represents a questionnaire-derived response, not an observed future university withdrawal.

### Multinomial Naive Bayes

**Task:** Classify reported professional help-seeking responses.

### Saved Results

| Metric | Value |
|:---|---:|
| Test observations | 21 |
| Accuracy | 28.6% |
| Weighted F1-score | 0.26 |

The saved classification report shows weak performance across the four reported classes.

### Decision Tree and Random Forest

**Task:** Classify a binary label derived from reported professional help-seeking responses.

### Saved Results

| Model | Accuracy | Positive-Class Recall | Positive-Class F1 |
|:---|---:|---:|---:|
| Decision Tree | 76.2% | 0.40 | 0.44 |
| Random Forest | 76.2% | 0.40 | 0.44 |

Both models produce the same recorded classification report.

### Critical Interpretation

The 76.2% accuracy should not be interpreted as strong identification of psychological support needs.

In the test data, the positive class contains only five observations, and the models correctly identify two of them.

The labels are derived from questionnaire answers about seeking or receiving help, not from a professional clinical assessment of whether help is needed.

---

## 14. Complementary Mental Health Disorders Notebook

The second notebook is:

`Analisis_Trastornos_Mentales.ipynb`

It focuses on descriptive analysis of mental health indicators across Mexican federal entities.

### Main Analyses

**National depression trend**

Explores annual depression-related indicators at the national level.

**Comparison by sex**

Compares recorded male and female rates.

**State ranking**

Identifies states with high recorded rates in 2023.

**Comparison between disorders**

Examines selected mental and behavioral disorder categories.

**Regional analysis**

Groups states into geographic regions for exploratory comparisons.

**Historical ranking**

Identifies years with relatively high recorded national rates.

### Data Dependency

This notebook expects:

```text
/content/mental_salud_limpio.xlsx
```

The cleaned dataset must be available before execution.

---

## 15. Technologies Used

| Technology | Purpose |
|:---|:---|
| Python | Programming language |
| Pandas | Data preparation and analysis |
| NumPy | Numerical computing |
| Matplotlib | Statistical visualization |
| Seaborn | Exploratory data analysis |
| Scikit-learn | Machine learning models and evaluation |
| K-Means | Exploratory clustering |
| Decision Tree | Regression and classification |
| Random Forest | Ensemble classification |
| SVM | Survey response classification |
| Multinomial Naive Bayes | Multiclass classification |
| Statsmodels | Exponential smoothing |
| GeoPandas | Geographic analysis |
| Shapefile | Geographic boundaries |
| Google Colab | Cloud execution |
| Jupyter Notebook | Interactive analysis |

---

## 16. Project Files and Resources

### Shared Research Folder

[Open the Google Drive Research Folder](https://drive.google.com/drive/folders/19m9xrpvTypQDonmSTG4Wks-zC5gT127t?usp=sharing)

The folder contains the source materials used in the research, including spreadsheets, mortality-related files, geographical information, and reference documents.

Access to individual files depends on the permissions configured by the folder owner.

### Complete Project Archive

**File:** `proyecto_depresion_estudiantil.zip`

The archive is intended to organize the project materials and supporting research files.

### Research Presentation

**File:** `presentación_depresión_estudiantil.pdf`

The presentation provides an additional way to communicate the project's purpose, analytical methodology, and research findings.

### Original Research Notebooks

- `LB_DATOS_DEPRESION_Y_SUICIDIO_ESTUDIANTIL_MEXICO.ipynb`
- `Analisis_Trastornos_Mentales.ipynb`

---

## 17. How to Run

### Requirements

- Python 3.
- Google Colab or Jupyter Notebook.
- Compatible source datasets.
- Required Python libraries.

### Install Core Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels geopandas openpyxl xlrd notebook
```

### Execution Steps

1. Download the authorized research datasets.
2. Open the main notebook.
3. Upload the required Excel files.
4. Execute the data preparation sections.
5. Review the descriptive statistical results.
6. Run the geographic visualization exercises.
7. Explore the historical youth suicide trends.
8. Examine the university student survey section.
9. Review the machine learning evaluation results.
10. Open the complementary notebook.
11. Load `mental_salud_limpio.xlsx`.
12. Execute the national and state-level descriptive analyses.

### Reproducibility Notes

The notebooks were developed through several experimental stages.

Some sections reuse variables such as `df`, `X_train`, and `y_train` for different datasets and modeling tasks.

For reliable execution, each analytical section may need to be run in a clean environment with its corresponding input data.

The supplementary notebook contains transformations that depend on the structure of the cleaned Excel file.

---

## 18. Research Limitations

### Data Provenance

The source, reporting methodology, and denominator of each statistical indicator must be verified before making epidemiological claims.

### Population Differences

National youth suicide records and university student survey responses refer to different populations.

They should not be interpreted as interchangeable datasets.

### Student Survey Sample

The university questionnaire uses a small, non-representative sample.

### Clinical Validation

The survey variables do not establish clinical diagnoses of depression, anxiety, or suicide risk.

### Classification Targets

Machine learning targets are derived from self-reported questionnaire answers rather than externally validated clinical or educational outcomes.

### Small Test Sets

Several models are evaluated using only 21 test observations.

### Label Encoding

Categorical responses are converted to integer labels, which can introduce arbitrary ordinal relationships.

### Generalization

Model accuracy does not establish reliable performance for new student populations.

### Time Series Forecasting

Forecast examples do not include adequate out-of-sample validation.

### Privacy

Mental health survey data must be handled with special care because participants may be identifiable through combinations of personal attributes.

### Causal Interpretation

Statistical associations cannot establish that particular educational, economic, or family circumstances cause depression or suicide.

---

## 19. Ethical and Responsible Use

This repository addresses sensitive mental health and suicide-related topics.

Its purpose is to support educational research, statistical literacy, and responsible data analysis.

The models should not be used to:

- Diagnose mental health conditions.
- Identify students as suicidal.
- Determine clinical treatment.
- Make disciplinary or admissions decisions.
- Deny educational opportunities.
- Replace professional psychological assessment.

Any future operational application would require appropriate ethical review, data protection, rigorous validation, and qualified professional oversight.

---

## 20. Future Improvements

Potential developments include:

- Documenting source data definitions and provenance.
- Separating the notebooks into reproducible research modules.
- Validating survey data collection procedures.
- Removing personally identifying information.
- Improving missing-data handling.
- Using validated psychological assessment instruments where appropriate.
- Applying stratified evaluation to classification models.
- Implementing cross-validation.
- Comparing models against simple baselines.
- Testing generalization on independent datasets.
- Improving temporal forecasting validation.
- Strengthening geospatial data integration.
- Creating interactive research visualizations.
- Developing an anonymized public research dataset where authorized.

---

## 21. Practical Research Applications

The project explores techniques relevant to:

- Public health data analysis.
- Student well-being research.
- Educational analytics.
- Statistical visualization.
- Mental health indicator monitoring.
- Geographic information analysis.
- Machine learning education.
- Responsible Data Science.

These are research applications of the analytical methods, not validated clinical capabilities of the current project.

---

## 22. Conclusion

This project combines two notebooks to examine mental health indicators, depression-related data, youth suicide mortality trends, and university student well-being in Mexico.

The analyses demonstrate the use of Python for data preparation, statistical visualization, clustering, regression, geographic exploration, time series forecasting, and classification.

Historical youth suicide data is explored through national and regional trends, while a university student survey provides an additional educational case study involving academic and emotional experiences.

The machine learning experiments illustrate classification methods but also reveal important limitations related to sample size, label definitions, and generalization.

Overall, the project provides a foundation for further research in public health analytics, educational data science, and responsible artificial intelligence.

---

## 23. Research References

### Research Data and Supporting Materials

[Shared Google Drive Folder](https://drive.google.com/drive/folders/19m9xrpvTypQDonmSTG4Wks-zC5gT127t?usp=sharing)

### National Institute of Statistics and Geography

[INEGI — Mexico](https://www.inegi.org.mx/)

### World Health Organization

[WHO — Mental Health](https://www.who.int/health-topics/mental-health)

### Scikit-learn

[Scikit-learn Documentation](https://scikit-learn.org/stable/)

### GeoPandas

[GeoPandas Documentation](https://geopandas.org/)

These external resources provide background and technical references. Their inclusion does not imply endorsement or independent validation of the research results.

---

## Author

**Data Engineer Luis Barahona**

Mexican Data Engineer and 2026 graduate of Universidad del Caribe, interested in Data Engineering, Data Science, Artificial Intelligence, public health analytics, and responsible applications of technology.

---

## Contact

| Platform | Contact |
|:---|:---|
| Email | [190300395@ucaribe.edu.mx](mailto:190300395@ucaribe.edu.mx) |
| GitHub | [github.com/LuisBarahonaMX](https://github.com/LuisBarahonaMX) |
| LinkedIn | [linkedin.com/in/luis-barahona-mx](https://www.linkedin.com/in/luis-barahona-mx/) |
| Instagram | [@luisbarahonamx](https://www.instagram.com/luisbarahonamx/) |
| X | [@luisbarahonaMX](https://x.com/luisbarahonaMX) |
| Website | [SIKO AI Platform](https://sikoai.web.app/) |
