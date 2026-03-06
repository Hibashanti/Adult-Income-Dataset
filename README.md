# Adult-Income-Dataset

Author: Hiba Shanti

This project analyzes the Adult Income dataset to predict whether an individual earns more than $50K per year based on demographic, educational, and financial attributes.

Dataset: https://www.kaggle.com/datasets/wenruliu/adult-income-dataset

 ### Data Cleaning and Visualization

I performed a comprehensive Exploratory Data Analysis (EDA), starting with data cleaning to remove duplicates, and used .info() and .describe() to inspect the structure and summary statistics. checked on missing values and resolved inconsistencies, and removed redundant features. Once the data was refined, I utilized data visualization techniques to examine feature relationships and uncover key patterns, ensuring a high-quality dataset for production.

Examples of visualized relationships:

- 1- Visualizing the capital gain and capital loss columns separately.
  
<img width="1191" height="490" alt="Screen Shot 2026-03-02 at 4 12 00 PM" src="https://github.com/user-attachments/assets/f8d9a808-e85b-47b2-ac02-ccae8665d76a" />

The boxplots of capital-gain and capital-loss reveal highly skewed distributions. In both features, the majority of individuals report a value of 0, indicating no investment-related gains or losses. However, a small subset of individuals shows extremely high values, resulting in significant outliers and long right tails.

This pattern suggests that investment activity is rare but strongly concentrated among a limited group of individuals.

- 2-Visualizing the relationship between workclass features and income.

   <img width="596" height="389" alt="Screen Shot 2026-03-02 at 4 29 26 PM" src="https://github.com/user-attachments/assets/5f3b946b-028e-43e8-88d0-21dfdcacbf5b" />

The visualization shows that workclass influences income levels, with most categories dominated by individuals earning ≤50K. However, Self-emp-inc stands out, as it has a noticeably higher proportion of individuals earning >50K compared to other work classes.


### Modeling Step

- During the modeling phase, the dataset was split into train and test data, then the X_train data were separated into categorical and numerical features. Missing values were imputed, categorical features were encoded, and numerical features were scaled when appropriate. Separate preprocessing pipelines were created for each feature type and combined using a ColumnTransformer to ensure consistent and reproducible data preparation.

- The preprocessed data were first trained using a default RandomForestClassifier model.
- The model achieves 98% accuracy on the training data, with very high precision and recall for both classes (F1-score ≈ 0.99 for ≤50K and 0.96 for >50K). However, performance drops on the test set to 83% accuracy, indicating some overfitting.
- On unseen data, the model performs well for the ≤50K class (F1-score = 0.89), but performance is weaker for the >50K class (F1-score = 0.63), with recall dropping to 0.58. This suggests the model is better at identifying lower-income individuals than correctly detecting higher-income cases,

#### Top important features 

- Permutation importance was used to measure how much model performance decreases when each feature is shuffled. The top 10 features were extracted and visualized in a bar chart.

<img width="505" height="347" alt="Screen Shot 2026-03-02 at 5 07 29 PM" src="https://github.com/user-attachments/assets/62962b07-ce76-43cf-a4bf-5040213242a4" />

-  Feature importance aligns with economic intuition: capital-gain is the strongest predictor, reflecting the link between investment income and higher earnings, followed by capital-loss, marital-status, and education level, which all indicate financial stability and earning potential.

  - Example of the relationship between two of the most important features and the target

   - The first graph visualizes the relationship between the target and the marital status, the graph shows that married individuales have a much higher probability of earning >50K compared to others.
   
<img width="795" height="491" alt="Screen Shot 2026-03-02 at 5 11 32 PM" src="https://github.com/user-attachments/assets/42346b4e-44c9-46b8-9ae9-aff9238af702" />

  - The second graph visualizes the relationship between the target and the occupation, it shows that certain occupations, such as Exec-managerial, Prof-specialty, Protective-serv, Armed-Forces, have more income than the other jobs. The reason some occupations may have higher income than others is that they require higher education, specialized skills, and leadership roles, so higher salaries are expected. whereas the remaining jobs might be manual labor, entry-level, with lower skill requirements.
    
 <img width="990" height="606" alt="Screen Shot 2026-03-02 at 5 12 49 PM" src="https://github.com/user-attachments/assets/707c565d-ca4c-4168-a324-26b3a30d53f0" />

 #### Features Selection 
 - We applied a feature engineering step to create additional meaningful features and then used an embedded method to select the most important ones for the model. The resulting Random Forest model showed that the training and test scores were very close, indicating that the model is not overfitting. However, to further improve performance and optimize predictive accuracy, we used GridSearchCV to tune the model’s hyperparameters, thereby enhancing overall effectiveness.

