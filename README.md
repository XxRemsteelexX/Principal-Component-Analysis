# Principal Component Analysis - Housing Price Prediction

## Project Overview

This repository contains a comprehensive Principal Component Analysis (PCA) implementation for predicting housing prices using dimensionality reduction techniques. The project demonstrates advanced statistical methods for handling multicollinearity and reducing feature space while maintaining predictive power.

## Dataset Description

The analysis uses a housing dataset with 7,000 property records containing comprehensive property information. The dataset includes 22 features with the target variable being property sale price.

### Key Features Analyzed
- **SquareFootage**: Living area in square feet (550 - 2,875 sq ft)
- **NumBathrooms**: Number of bathrooms (1.0 - 5.8)
- **NumBedrooms**: Number of bedrooms (1 - 7)
- **RenovationQuality**: Quality of renovations (0.01 - 10.0 scale)
- **DistanceToCityCenter**: Distance to city center in miles (0 - 65 miles)
- **AgeOfHome**: Property age in years (0 - 179 years)

### Dataset Characteristics
- **Size**: 7,000 observations, 22 variables
- **Target Variable**: Price ($85,000 - $1,046,676)
- **Missing Values**: None
- **Feature Selection**: 6 key numerical features for analysis

## Project Structure
```
Principal-Component-Analysis/
├── pca_analysis.ipynb              # Main PCA analysis notebook
├── pca_analysis_extended.ipynb     # Extended analysis with additional methods
├── housing_dataset.csv             # Complete housing dataset
├── cleaned_dataset.csv             # Standardized dataset for analysis
├── training_dataset.csv            # PCA-transformed training data
├── test_dataset.csv                # PCA-transformed test data
├── pca_env/                        # Virtual environment
└── README.md                       # Project documentation
```

## Methodology

### 1. Data Preprocessing
- **Feature Selection**: Chose 6 key numerical features based on domain knowledge
- **Standardization**: Applied StandardScaler to normalize all features
- **Missing Value Check**: Verified data completeness

### 2. Principal Component Analysis
- **Dimensionality Assessment**: Analyzed all 6 components initially
- **Scree Plot Analysis**: Visual inspection of explained variance
- **Elbow Method**: Determined optimal number of components
- **Component Retention**: Selected 5 principal components

### 3. Component Analysis Results

#### Explained Variance by Component
| Component | Eigenvalue | Individual Variance | Cumulative Variance |
|-----------|------------|-------------------|-------------------|
| **PC1** | 2.1543 | 35.91% | 35.91% |
| **PC2** | 1.2847 | 21.41% | 57.32% |
| **PC3** | 0.9234 | 15.39% | 72.71% |
| **PC4** | 0.8123 | 13.54% | 86.25% |
| **PC5** | 0.5892 | 9.82% | 96.07% |

#### Component Interpretation
- **PC1** (35.91%): Property size and quality factors
- **PC2** (21.41%): Location and accessibility features  
- **PC3** (15.39%): Property age and renovation status
- **PC4** (13.54%): Bathroom and bedroom configuration
- **PC5** (9.82%): Neighborhood characteristics

## Model Performance

### Linear Regression with PCA Components

#### Performance Metrics
- **Training R²**: 0.554 (55.4% variance explained)
- **Adjusted Training R²**: 0.554
- **Test R²**: 0.508 (50.8% variance explained)
- **Training RMSE**: $101,054
- **Test RMSE**: $102,090

#### Regression Equation
```
Price = 308,142.77 + (78,641.91 × PC1) + (23,489.89 × PC2) + 
        (16,635.44 × PC3) + (4,890.77 × PC4) + (7,855.54 × PC5)
```

#### Statistical Significance
All principal components show statistical significance (p < 0.001), indicating strong predictive power.

## Key Findings

### Benefits of PCA Implementation
1. **Dimensionality Reduction**: Reduced from 6 to 5 components while retaining 96% variance
2. **Multicollinearity Elimination**: Principal components are orthogonal by design
3. **Noise Reduction**: Filtered out 4% of variance attributed to noise
4. **Interpretable Components**: Clear factor loadings for business understanding

### Component Contributions
- **PC1 dominates** with highest coefficient (78,642), representing overall property quality
- **PC2 and PC3** provide substantial additional predictive power
- **PC4 and PC5** contribute moderate but statistically significant effects
- **Conservative approach**: Retained 5 components for robust model performance

### Model Strengths
- Strong explained variance (50.8% on test set)
- Consistent performance between training and test sets
- All components statistically significant
- Effective handling of feature correlations

### Model Limitations
- Moderate R² suggests room for improvement with additional features
- Linear relationship assumption may miss non-linear patterns
- Limited to selected numerical features only

## Requirements

```python
pandas >= 1.3.0
numpy >= 1.21.0
scikit-learn >= 0.24.0
matplotlib >= 3.4.0
seaborn >= 0.11.0
statsmodels >= 0.12.0
scipy >= 1.7.0
jupyter >= 1.0.0
```

## Installation & Usage

### Setting Up Environment
```bash
# Create virtual environment
python3 -m venv pca_env

# Activate environment
source pca_env/bin/activate  # Linux/Mac
# or
pca_env\Scripts\activate     # Windows

# Install dependencies
pip install pandas numpy scikit-learn matplotlib seaborn statsmodels scipy jupyter
```

### Running the Analysis
```bash
# Start Jupyter notebook
jupyter notebook pca_analysis.ipynb
```

## Technical Implementation

### PCA Workflow
1. **Data Loading**: Import housing dataset
2. **Feature Selection**: Choose relevant numerical variables
3. **Standardization**: Apply StandardScaler transformation
4. **PCA Fitting**: Compute principal components
5. **Component Selection**: Apply elbow method
6. **Model Training**: Linear regression on components
7. **Evaluation**: Performance metrics and interpretation

### Advanced Features
- **Correlation Analysis**: Heatmap visualization of original features
- **Scree Plot**: Visual component selection guide  
- **Component Matrix**: Factor loadings interpretation
- **Statistical Testing**: P-value analysis for significance
- **Cross-validation**: Train/test split for robust evaluation

## Results Interpretation

### Principal Components Factor Loadings
The component matrix reveals how original features contribute to each principal component:
- **High loadings** indicate strong feature influence on component
- **Component interpretation** provides business insights
- **Orthogonal components** eliminate multicollinearity concerns

### Comparison to Original Features
- PCA reduces dimensionality while preserving most information
- Components capture underlying data structure
- Model performance comparable to full feature set
- Improved interpretability through factor analysis

## Future Enhancements

1. **Non-linear PCA**: Implement kernel PCA for non-linear relationships
2. **Feature Engineering**: Include categorical variables with encoding
3. **Advanced Models**: Test with Random Forest, SVM on components
4. **Cross-validation**: Implement k-fold CV for robust estimates
5. **Component Visualization**: 2D/3D plots for data exploration
6. **Automated Selection**: Implement multiple component selection criteria

## Files Description

- **pca_analysis.ipynb**: Complete PCA analysis with linear regression modeling
- **pca_analysis_extended.ipynb**: Extended analysis with additional statistical methods
- **housing_dataset.csv**: Original dataset with all property features
- **cleaned_dataset.csv**: Standardized features ready for PCA
- **training_dataset.csv**: PCA-transformed training data with target variable
- **test_dataset.csv**: PCA-transformed test data for model evaluation

## Statistical Validation

### Assumptions Verified
1. ✅ **Linear Relationships**: Reasonable linear associations observed
2. ✅ **Feature Standardization**: All variables normalized for PCA
3. ✅ **Component Orthogonality**: Principal components uncorrelated by design
4. ✅ **Statistical Significance**: All components show p < 0.001

### Model Diagnostics
- **Residual Analysis**: Acceptable error distribution
- **Variance Explained**: 96% of original variance retained
- **Component Stability**: Consistent loadings across analysis
- **Predictive Validity**: Strong test set performance

## Author

Principal Component Analysis Project

## License

This project is for educational and research purposes.