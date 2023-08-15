# Recipe-Recommender-System
The performance of a recommendation engine will significantly impact the revenue your recipe site can generate.  Designing a recommender from scratch is a time-consuming task. To build a recommender system that will have to generate recommendations for given user_ids. Recommender systems in real life are expected to come up with results instantaneously. Imagine you are surfing YouTube and the recommendations panel to the right of the screen takes 20 minutes to load. That would not be a good experience, and you might decide to use another video streaming service. In the world of recommenders, prediction latency is more important than accuracy. Moreover, the data and features these recommender systems use to make recommendations are very voluminous. The data we used for EDA in the earlier assignment is not on the same scale as the YouTube recommender's data.

The recommendation engine is a way to increase the website's user engagement. If a user is shown relevant recipes, they are more likely to spend more time on your site reading about recipes. Higher user engagement will likely result in more business opportunities like collaborations, promotions, etc.
The performance of a recommendation engine will significantly impact the revenue your recipe site can generate. Designing a recommender from scratch is a time-consuming task.

### Data Source:

# raw recipe data
s3a://raw-recipes-clean-upgrad/RAW_recipes_cleaned.csv

# raw ratings data
s3a://raw-interactions-upgrad/RAW_interactions_cleaned.csv

The first file is the Raw_recipes.csv file. It contains all the recipe-related information. Each row in this file describes a recipe. The fields available in the data are described below.
The second file we will be using is the RAW_interactions.csv. Each row in this data file is one user reviewing one recipe. One user can review more than one recipe, and each recipe can be reviewed by more than one user, so there is a many-to-many relationship between users and recipes, but the combination of user_id and reviewer_id in each row will be unique


# Downloadable data links 

https://raw-recipes-clean-upgrad.s3.amazonaws.com/raw_ratings_small.csv

https://raw-recipes-clean-upgrad.s3.amazonaws.com/raw_recipies_small.csv

https://raw-recipes-clean-upgrad.s3.amazonaws.com/RAW_recipes_cleaned.csv


# S3 bucket links 

s3a://raw-recipes-clean-upgrad/raw_ratings_small.csv

s3a://raw-recipes-clean-upgrad/raw_recipies_small.csv

s3a://raw-recipes-clean-upgrad/RAW_recipes_cleaned.csv


The data file above has the same structure as the data file from the first part of the project. You can refer to the data dictionary from the last project. The data attached here does not have the new features you created earlier, so you must recalculate the features if needed. 

You are expected to use the Spark platform to build your ML model. The algorithms you will use are ALS and K Nearest Neighbors (KNN).

### Machine Learning Models
#### ALS
Spark natively has the ALS algorithm in its libraries. You will have to massage input data to be in the form the algorithm expects. Also, a word of caution here. The more columns there are in the training data, the higher the training time, so be careful while massaging the data and calling the fit statement on a data set with a large number of columns. 

### KNN (Optional)
Spark natively does not support the KNN algorithm because it is not an easily parallelized algorithm. You will be using an algorithm called HNSW. it is an approximation of the KNN algorithm
### Ensemble strategies
the ALS algorithm produces recommendations based on ratings. The numerical output of ALS is on the same scale as the label data. In our case, the label is the rating a particular user gives a recipe. The ALS will predict a specific user's recipe rating (on a scale of 0 to 5) and then use the predicted ratings to make recommendations. The numerical output, in this case, is on a scale of 0 to 5. In contrast, the KNN model will use the distance (specifically cosine distance) to make recommendations. The numerical predictions of both algorithms are on different scales.
