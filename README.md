# Credit Card Customer Segmentation (K-Means Clustering)

A reproducible data science project that applies K-Means clustering to segment credit card customers by financial and demographic attributes. The segmentation helps financial institutions tailor products, improve risk assessment, and design targeted marketing strategies.

## Table of Contents
- [Overview](#overview)
- [Highlights](#highlights)
- [Technologies](#technologies)
- [Project Structure](#project-structure)
- [Data Preprocessing & Feature Engineering](#data-preprocessing--feature-engineering)
- [Modeling & Evaluation](#modeling--evaluation)
- [Using the Model (Predicting New Customers)](#using-the-model-predicting-new-customers)
- [Results & Visualizations](#results--visualizations)
- [How to Run](#how-to-run)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview
This project demonstrates customer segmentation using K-Means clustering on a credit-card-customer dataset. The workflow includes cleaning, feature engineering, encoding, scaling, selecting an optimal number of clusters (Elbow Method), and profiling the resulting clusters with meaningful, human-readable labels.

## Highlights
- Robust preprocessing pipeline (missing values, categorical encoding, scaling)
- Thoughtful feature engineering to capture household and employment characteristics
- StandardScaler for feature normalization
- K-Means clustering with Elbow Method to determine optimal k (selected k = 4)
- Cluster profiling and human-readable cluster names
- Reusable prediction function for new customers

## Technologies
- Language: Python
- Libraries: pandas, numpy, scikit-learn, matplotlib, seaborn
- Notebook: Jupyter Notebook
- Version control: Git, GitHub

## Project Structure
DataScienceProject/
│
├── Notebook/
│     └── Credit_Card_Clustering.ipynb
│
├── README.md
├── .gitignore
└── requirements.txt (optional)

## Data Preprocessing & Feature Engineering
Key preprocessing steps implemented in the notebook:
- Missing values:
  - Fill `OCCUPATION_TYPE` with `"Unknown"`
  - Other missing-value strategies applied as needed per column
- Categorical encoding:
  - One-hot encoding for categorical variables
- Feature scaling:
  - StandardScaler applied to numeric features to normalize ranges
- Derived features:
  - AGE — calculated from birth or provided date fields
  - EMP_YEARS — converted and standardized employment duration
  - INCOME_PER_MEMBER — total income divided by household size
  - CHILD_RATIO — number of children divided by household size

These engineered features improve cluster separability and interpretability.

## Modeling & Evaluation
- Algorithm: K-Means clustering
- Approach:
  - Standardize numeric features with StandardScaler
  - Evaluate optimal number of clusters using the Elbow Method (inertia plot)
  - Final model trained with k = 4 based on the Elbow analysis
- Final clusters and human-readable labels:
  - 0 — Young Working Families
  - 1 — Elderly Retirees
  - 2 — High-Income Professionals
  - 3 — Middle-Age Moderate Households

Cluster profiling includes means/medians of key numeric features and category-wise proportions to describe each segment.

## Using the Model (Predicting New Customers)
A reusable prediction function is included in the notebook to make predictions for new customers after preprocessing to the same feature template and scaling. Example usage:

```python
# new_customer: dict or DataFrame row with raw features
# feature_template: DataFrame or template used to align features (one-hot columns, etc.)
# scaler: fitted StandardScaler from training
# kmeans: fitted KMeans model from training

cluster_number = predict_cluster(new_customer, feature_template, scaler, kmeans)

cluster_names = {
    0: "Young Working Families",
    1: "Elderly Retirees",
    2: "High-Income Professionals",
    3: "Middle-Age Moderate Households",
}

print("Cluster:", cluster_names[cluster_number])
```

Make sure to apply the same preprocessing steps and one-hot encoding schema before calling the prediction function.

## Results & Visualizations
The notebook provides visual and tabular explorations, including:
- Elbow Method plot (inertia vs. number of clusters)
- Cluster counts and relative sizes
- Cluster-wise numeric feature means for quick comparison
- Category-wise proportion plots (e.g., education level, occupation type)
- Top distinguishing features per cluster for interpretability

These visualizations support business interpretation and downstream decision-making.

## How to Run
1. Clone the repository:
   git clone https://github.com/SarwarRimon/DataScienceProject.git

2. (Optional) Create and activate a virtual environment:
   python -m venv venv
   source venv/bin/activate  # macOS / Linux
   venv\Scripts\activate     # Windows

3. Install dependencies:
   pip install -r requirements.txt

4. Open and run the notebook:
   jupyter notebook Notebook/Credit_Card_Clustering.ipynb

Notes:
- The notebook is interactive and documents each preprocessing and modeling step.
- If your dataset filename differs from the notebook defaults, update the path at the top of the notebook.

## Contributing
Contributions are welcome! For major changes, please open an issue to discuss the proposed change. Small improvements can be submitted as pull requests. Suggestions:
- Add unit tests for preprocessing functions
- Modularize preprocessing and modeling into Python scripts / package
- Add integration tests for the prediction function

## License
This project is released under the MIT License. See LICENSE for details.

## Contact
Maintainer: Sarwar Rimon  
Repository: https://github.com/SarwarRimon/DataScienceProject

Acknowledgements: Thank you to all contributors and the open-source community for tools and resources used in this project.
