# Heart Disease prediction
Heart disease describes a range of conditions that affect your heart. Diseases under the heart disease umbrella include blood vessel diseases, such as coronary artery disease, heart rhythm problems (arrhythmias) and heart defects you’re born with (congenital heart defects), among others. Heart disease is one of the biggest causes of morbidity and mortality among the population of the world. Prediction of cardiovascular disease is regarded as one of the most important subjects in the section of clinical data analysis. The amount of data in the healthcare industry is huge.

Machine learning (ML) proves to be effective in assisting in making decisions and predictions from the large quantity of data produced by the healthcare industry. All machine learning workflows depend on feature engineering, which comprises feature extraction and feature selection that are fundamental building blocks of modern machine learning pipelines.  

Our project focusses on applying different feature selection methods like Filter-based methods, wrapper, Embedded methods and Genetic Algorithms to reduce the high dimensional heart disease dataset and understand how it affects the accuracy of Machine Learning algorithms. We have further also explored Genetic algorithm and used it for hyperparameter tuning for two models viz. Support Vector Machine (SVM) and Neural networks to find optimal values of C, gamma and number of neurons, number of hidden layers, learning rate and momentum respectively on different datasets to predict heart disease.

## Cardiac Arrythmia detection
The first dataset was of Arrhythmia Heart disease. It consisted of 280 columns and 452 rows.  It’s a categorical problem as we need to predict the last column viz class, which consisted of two categorical values 0 and 1. “0” means person has the disease and “1” means no disease. It can be seen from the number of columns that it’s a higher dimensional data. We chose feature selection to select the best possible feature combination to maximise result and efficiency of our model.
In Arrhythmia dataset, following steps were performed by us-  

**1. Filter Based (Basic) Feature Selection:** 

- Removed Constant features – The Constant features do not provide any information for classification. They have same value for output. Therefore, they should be removed.  22 features were constant in this dataset, and they were removed. 

- Removed Quasi Constant features – Quasi constant features are nearly constant; they provide same output for very large sample of dataset. Thus, they are also not important. In this dataset there were 43 quasi constants. Here we kept variance threshold as 0.01. And removed features those features. After that 214 feature were left. 

- Removed Duplicate features – Duplicate features need not be used in model; it would incur unnecessary computation. There were 2 duplicate features and were dropped for further processing.  

**2. Filter Based (Correlated) Feature Selection:** 

- Removed Correlated features – Features which are correlated also incur unnecessary storage and speed. As they are correlated, it’s better to have only one of them. We used Spearman method here as it gave the best results. There were 5 features which were 99% correlated. The appropriate algorithm has been used to remove them. 

**3. Statistical Based Feature Selection:**

- Removed Univariate features– Univariate feature selection examines the impact of each feature on target variable. We used Decision tree Classifier to find ROC-AUC score. The features which had ROC-AUC score less than or equal to 5 were removed.  

**4. Embedded Method:** - Performed Lasso regularization

**5. Wrapper based Feature Selection:**
-  Step Forward Feature Selection – In this method the best combination of features is identified by forward approach.

We trained our data using 5 models viz K Nearest Neighbours, Logistic Regression, SVM, Random Forest and Decision tree Classifier.

## Genetic Algorithm (SVM and NN)
### Cleveland Dataset
Genetic Algorithm provided the basis for Feature selection in our approach for this dataset. Genetic algorithm has a mechanism which works on the survival of the fittest. The basic steps involved are selection of mating pool, cross over, mutation. Here, we took random binary digits 0 and 1 as encoded features. 0 meant feature was not selected and 1 meant it had been selected. Below are the values considered:
- p_c = 1 which was probability of crossover, since we always want crossover to occur, 
- p_m = 0.2 which was probability of mutation.

We got best results with 80 population and we applied GA for 30 generations. Further, SVM classifier was used to obtain the objective function.

Hyperparameter Tuning - Hyperparameters tuned were gamma and C for SVC model. 

### Alizadeh Sani Dataset
Genetic Algorithm provided the basis for Feature selection in our approach for this dataset. Genetic algorithm has a mechanism which works on the survival of the fittest. The basic steps involved are selection of mating pool, cross over, mutation. Here, we took random binary digits 0 and 1 as encoded features. 0 meant feature was not selected and 1 meant it had been selected. Below are the values considered:
- p_c = 1 which was probability of crossover, 
- p_m = 0.2 which was probability of mutation. 

We got best results with 50 population and we applied GA for 30 generations. Here, MLP classifier was used to obtain the objective function.

Hyperparameter Tuning - Hyperparameters tuned were learning rate, momentum, number of neurons and number of hidden layers for MLP model. Solver type was Adam.
