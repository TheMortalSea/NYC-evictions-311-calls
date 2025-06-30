# NYC Evictions and 311 Calls Prediction Model

![NYC Evictions](assets/NYCevictions.png.png)
![NYC 311 calls](assets/NYC311%20Calls.png)

A machine learning project analyzing the predictive power of NYC 311 Housing Complaint calls for eviction counts in Manhattan, incorporating socio-economic and housing-related factors.

## Project Overview

This study evaluates whether 311 housing complaint calls can serve as effective predictors for evictions in Manhattan, using machine learning models trained on demographic, economic, and housing data from 2023.

### Research Questions
- Can we properly train a model using 311 calls about housing and other studied predictors of eviction?
- Are 311 calls about housing conditions a good indicator for evictions in Manhattan?

## Key Findings

- **Random Forest model** achieved the best performance with RMSE of 4.51
- **311 housing complaints** showed high importance (0.78) in the Random Forest model
- All models significantly outperformed baseline predictions
- Study focused on 312 Manhattan census tracts with residential rental units

## Methodology

### Models Implemented
1. **Tweedie Regression** - Handles overdispersion in count data
2. **Random Forest** - Captures complex non-linear relationships
3. **Baseline Models** - Naive (intercept-only) and Poisson regression for comparison

### Performance Metrics
| Model | RMSE | MSE | MAE | AIC |
|-------|------|-----|-----|-----|
| Random Forest | 4.51 | 21.25 | 3.32 | 223.12 |
| Tweedie | 5.38 | 32.15 | 3.64 | 1415.59 |
| Poisson | 5.24 | 29.72 | 3.71 | 1622.08 |
| Naive | 7.22 | 52.11 | 5.35 | 1951.08 |

## Data Sources

### Primary Datasets
- **NYC 311 Housing Complaints** (NYC Open Data)
- **Eviction Records** (NYC Open Data)
- **Demographics & Socioeconomics** (American Community Survey 5-year estimates)
- **Vacancy Rates** (Decennial Census Survey)
- **Geographic Boundaries** (US Census Bureau)
- **Housing Distribution** (NYC Pluto dataset)

### Key Variables
- **Target Variable**: Eviction counts per census tract
- **Primary Predictor**: 311 housing complaint calls
- **Control Variables**: 
  - Race/ethnicity demographics
  - Household income and poverty rates
  - Rent burden (contract rent)
  - Housing availability (total & vacant units)

## Temporal Scope

**Focus Year: 2023**
- First post-COVID year showing data stabilization
- Post-Housing Stability and Tenant Protection Act (2019)
- Avoids COVID-19 eviction moratorium complications

## Data Processing

### Geographic Unit
- **Census Tracts** used to avoid inaccuracies of smaller block units
- Manhattan-specific analysis (312 residential census tracts)
- Point data (evictions, 311 calls) aggregated within census tracts using QGIS

### Data Cleaning
- Removed census tracts without residential zoning
- Addressed multicollinearity using Variance Inflation Factor (VIF < 10)
- Handled overdispersion in eviction count data (variance: 52.29, mean: 7.04)

## Technical Implementation

### Libraries Used
- `statsmodels` - Tweedie regression
- `scikit-learn` - Random Forest, GridSearchCV
- `QGIS` - Spatial data aggregation

### Model Optimization
- **Random Forest**: GridSearchCV with 10-fold cross-validation
- **Hyperparameter Tuning**: Minimized Mean Squared Error (MSE)
- **Validation**: Learning curves to minimize overfitting

## Results & Implications

### Feature Importance
- **311 Housing Calls**: High importance in Random Forest (0.78)
- **Median Income**: Significant predictor across all models
- **Housing Availability**: Key factor in eviction risk

### Interpretation Considerations
High 311 call volumes may indicate:
- Genuine housing problems increasing eviction risk
- Increased awareness and reporting behavior
- Limited access to alternative resources for housing concerns

## Limitations

1. **Spatial Accuracy**: Poor geocoding required census tract aggregation instead of precise point analysis
2. **Model Performance**: All models leave room for accuracy improvements
3. **Causation vs Correlation**: High 311 calls may reflect reporting behavior rather than housing quality

## Future Research

- Refine geocoding for more granular spatial analysis
- Expand to other NYC boroughs
- Incorporate temporal dynamics
- Explore additional housing quality indicators
- Develop real-time eviction risk monitoring system

## Academic Context

This project was completed as part of GEOG0115: Social Data Science at UCL Department of Geography (2024-25). The research contributes to understanding housing instability prediction and the utility of citizen-reported data (311 calls) in urban policy applications.

## Policy Relevance

Findings support the potential use of 311 housing complaint data for:
- Early identification of eviction-risk areas
- Targeted intervention programs
- Resource allocation for housing assistance
- Proactive tenant protection measures

---