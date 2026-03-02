# Adult-Income-Dataset

Author: Hiba Shanti

This project analyzes the Adult Income dataset to predict whether an individual earns more than $50K per year based on demographic, educational, and financial attributes.

Dataset: https://www.kaggle.com/datasets/wenruliu/adult-income-dataset

Data Cleaning and visualization: I performed a comprehensive Exploratory Data Analysis (EDA), starting with data cleaning to remove duplicates, and used .info() and .describe() to inspect the structure and summary statistics. checked on missing values and resolved inconsistencies, and removed redundant features. Once the data was refined, I utilized data visualization techniques to examine feature relationships and uncover key patterns, ensuring a high-quality dataset for production.

Examples of visualized relationships:

- 1- Visualizing the capital gain and capital loss columns separately.
- 
<img width="1191" height="490" alt="Screen Shot 2026-03-02 at 4 12 00 PM" src="https://github.com/user-attachments/assets/f8d9a808-e85b-47b2-ac02-ccae8665d76a" />

The boxplots of capital-gain and capital-loss reveal highly skewed distributions. In both features, the majority of individuals report a value of 0, indicating no investment-related gains or losses.However, a small subset of individuals shows extremely high values, resulting in significant outliers and long right tails.

This pattern suggests that investment activity is rare but strongly concentrated among a limited group of individuals.

- 2-# Visualizing the relationship between workclass feature and the income.

   <img width="596" height="389" alt="Screen Shot 2026-03-02 at 4 29 26 PM" src="https://github.com/user-attachments/assets/5f3b946b-028e-43e8-88d0-21dfdcacbf5b" />

The visualization shows that workclass influences income levels, with most categories dominated by individuals earning ≤50K. However, Self-emp-inc stands out, as it has a noticeably higher proportion of individuals earning >50K compared to other work classes.
