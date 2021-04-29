Predict TripAdvisor Rating
In this competition at Kaggle, we will have to predict the rating of a restaurant on TripAdvisor company.
 One of the company's problems is dishonest restaurants that wind up their ratings. One way to find such restaurants is to build a model that predicts the rating of the restaurant. If the predictions of the model are very different from the actual result, then the restaurant may not be playing fair and should be checked. The task is to create such a model.

Thus, we will create a model using machine learning algorithms.
Machine learning algorithm - RandomForestRegression.
Our task is to qualitatively prepare the data for training the model. Data cleaning and generation of new features (Feature Engineering) can significantly improve the accuracy of the model.

Goals and objectives of the project
The goal of this project is to prepare the data of the initial dataset for training the ML model, which will give the minimum error in predicting the restaurant rating.
To achieve this goal, you must complete the following tasks:
1. Load and clear data, process gaps.
2. Create new features that will improve the quality of modelling.
3. Conduct an EDA
4. Create ML models with the RandomForestRegression algorithm.
5. Train the model based on the prepared dataset
5. Get the minimum possible deviation of the forecast data from the actual values.

Dataset description
Let's look at the variables that the dataset contains:
The dataset contains data on 40,000 restaurants in Europe, and the model we will train will need to predict the restaurant rating from TripAdvisor based on the data in the dataset.
The initial version of the dataset consists of ten columns containing the following information:
Restaurant_id - identification number of the restaurant / restaurant chain;
City - the city where the restaurant is located;
Cuisine Style - cuisine or kitchens, which include the dishes offered in the restaurant;
Ranking - the place that this restaurant occupies among all restaurants in its city;
Rating - the rating of the restaurant according to TripAdvisor (this is the value the model should predict);
Price Range - the range of prices in the restaurant;
Number of Reviews - the number of reviews about the restaurant;
Reviews - data about two reviews that are displayed on the restaurant's website;
URL_TA - The URL of the restaurant's TripAdvisor page.
ID_TA is the identifier of the restaurant in the TripAdvisor database.

Conclusions:
In this project, a dataset with information on restaurants from TripAdvisor was analyzed and prepared for modeling. The job was to clean up the data, fill in the blanks, and create new features to reduce the restaurant rating prediction error. The categorical features have been converted to numerical format where possible for use in the ML model.
Data gaps were found in the dataset in the 'Number of Reviews', 'Price Range' and 'Cuisine Style' features. The gaps were filled in and new tags 'isNAN' were created with information about the absence of data.
The 'City' category includes 31 cities. Most restaurants (7193) are in London. The feature was coded using the get_dummies function.
The order attribute 'Price Range' - 3 gradations - was replaced by consecutive numbers 1,2,3. Most restaurants are in the middle price range.
Category feature 'Cuisine Style': 125 unique cuisines in the dataset. The most common are vegetarian and European. On its basis, a new feature has been created with the number of kitchens in the restaurant.
The dates of the reviews were extracted from the 'Reviews' tag. A feature has been created with a difference in days between two reviews, as well as a feature "review old age relative to the freshest in days".
A new attribute 'Relative_Ranking' has been created - the ratio of the restaurant's rank to the number of restaurants in this city according to the dataset. Important: in the end, this feature made the greatest contribution to improving the accuracy of modeling.
To create a new attribute 'Population', information on the population of cities in the dataset was found on the Internet and entered manually in the form of a dictionary. Based on this, new relative attributes have been created: 'Review to Population' (the ratio of the number of reviews to the population) and 'Rel_Rank to Population' (the ratio of the relative rank to the population).
The correlation matrix showed the absence of multicollinearity, so all features were left for further use in the ML model.
Simulations were performed using the "RandomForestRegression" machine learning algorithm. Rounding off the simulation results (down to 0.5 as the 'Rating' step in the original dataset) reduced the absolute error. The Mean Absolute Error metric showed a deviation of MAE = 0.16875 from the actual values. This is less than the MAE from the baseline notebook.
Thus, the processing and feature engineering described above gave their effect and increased the accuracy of the simulation.