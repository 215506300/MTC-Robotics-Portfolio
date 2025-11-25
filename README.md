Creation of a Multi-Regression Model
Problem
The project aimed to develop a predictive model for estimating car sale prices based on features like brand, model, year, condition, fuel type, mileage, horsepower, and more. Challenges included addressing distrust in car pricing (e.g., price gouging at dealerships), handling potential future impacts like tariffs on imports, dealing with skewed distributions (e.g., right-skewed sale prices under $40,000), outliers (e.g., illogical fuel economy or mileage for new cars), and selecting the best model from multiple regression techniques to achieve accurate, generalizable predictions.
Approach

Data Preprocessing: Loaded dataset from DataSet.xlsx using pandas. Removed irrelevant columns (Body Type, Style, Make). Handled outliers (e.g., Fuel Economy Average > Highway except for hybrids). Standardized new cars (Miles Driven=0, Title Status="Clean"). Engineered Car Age feature (2025 - Year) for better depreciation modeling.
Exploratory Data Analysis (EDA): Visualized distributions (e.g., right-skewed Sale Price), correlations (e.g., Car Age: -0.7, Miles Driven: -0.6 with Sale Price), and impacts (e.g., luxury brands like BMW/Mercedes priced higher; "Excellent" condition 30% above "Fair"). Used seaborn for heatmaps, violin plots, and pairplots to identify non-linear relationships.
Feature Engineering: Label-encoded ordinal features (Condition, Payment Status). One-hot encoded categorical features (Brand, Model, Color, etc.), expanding to 92 columns. Scaled numerical features with StandardScaler for model consistency.
Model Selection and Training: Split data into 70% train, 15% validation, 15% test. Trained baselines (Linear Regression) and advanced models (Decision Tree, Random Forest, XGBoost, KNN). Built ensembles: Voting Regressor (Linear + RF + XGBoost) and Bayesian weighted average. Evaluated with MAE, MSE, R².
Final Model: Bayesian Ensemble, combining top performers for robustness.

Results

Metrics: Bayesian Ensemble achieved MAE=79.58, MSE=12,870.31, R²=0.9999 on test set. Outperformed others (e.g., XGBoost: MAE=39.47, but ensemble better for outliers; Linear Regression: MAE=219.76).
Observations: Model excels on diverse cars (sedans to luxury), with ensembles handling volatility better. Skewed data and overrepresentation (e.g., BMW 3 Series: 225 entries) influenced luxury bias.

How to Run
Requirements

Python 3.12+
Libraries: pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost

Install dependencies:
textpip install pandas numpy matplotlib seaborn scikit-learn xgboost
Commands

Open Project-1 (1).ipynb in Google Colab or Jupyter Notebook.
Run all cells sequentially: Loads data, preprocesses, performs EDA, encodes/scales features, trains models, and evaluates.
For predictions: Use the Bayesian Ensemble (defined in notebook) on new data via bayesian_ensemble.predict(X_new).
Customize: Adjust train/test splits or add models in the training section.

No GPU needed; runs on CPU.
Data Access Notes

Dataset: DataSet (1).xlsx with ~10,000 rows, columns like Brand, Model, Year, Cylinders, Fuel Economy, Seats, Transmission, Horsepower, Fuel Type, Color, Miles Driven, Condition, Title Status, Damages, Number of Owners, Title Available, Payment Status, Sale Price. 1,450 unique Brand-Model-Year combos.
Size: Numerical features (e.g., Sale Price: $2,000-$57,060; Miles: 0-360,000); categorical (e.g., 11 brands like Mercedes, Subaru).
Access: Load via pd.read_excel('DataSet.xlsx'); no external download. Cleaned version created in notebook.

What I Learned / Next Steps

Learnings: Mastered end-to-end ML workflow: data cleaning for logical consistency, EDA for insights (e.g., depreciation via Car Age), encoding/scaling for categorical data, and ensemble methods for superior performance over single models. Understood trade-offs (e.g., XGBoost precision vs. ensemble robustness) and business applications (fair pricing amid market distrust/tariffs).
Next Steps:
Incorporate more data: Add external sources for real-time pricing or tariffs simulation.
Advanced modeling: Tune hyperparameters with GridSearchCV; try neural networks for non-linearities.
Deployment: Build a web app (e.g., Streamlit) for user input/predictions.
Handle biases: Balance dataset for underrepresented models; add features like location/economy indicators.
Evaluation: Compute cross-validation scores for better generalization.
