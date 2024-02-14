# Group-01 Content Based Receipe Filtering System

**Overview:**

This repository contains the code and documentation for a Recipe Recommendation System based on content-based filtering. The system leverages the characteristics and features of recipes to provide personalized recommendations. We have used the [Food.com Recipes and Interactions](https://www.kaggle.com/datasets/shuyangli94/food-com-recipes-and-user-interactions?select=RAW_recipes.csv) dataset from kaggle for our work.

**Data Analysis (Pre-processing/Insights):**

From the given dataset we have extensively worked with RAW_recipes.csv. The value insights that we got from the data analysis of the csv is as documented below :

*Summary of the dataset and features:*

Given data is a crawled data from Food.com (GeniusKitchen) online recipe aggregator. This dataset consists of 180K+ recipes and 700K+ recipe reviews covering 18 years of user interactions and uploads on Food.com (formerly GeniusKitchen). Each instance of the given dataset refers to a unique recipe along with its nutritious values and steps involved into making. In total there are 12 columns/features as summarised below:

*Summary of the data:*

1. name:

Each recipe have a name given by the creator. Name is the feature that represents this name. It is also useful to derive insights about the whole recipe in short.

2. id:

Unique ID of each recipe.

3. minutes:

It refers to the time that goes into making of that specific recipe.

4. contributor ID:

It is the unique ID of the person on the platform who contributed the recipe.

5. submitted:

The date on which the recipe was submitted.

6. tags:

Tags refer to the labels given to the recipe. It is in the form of a list that contains the whole aggregate of the tags for a specific recipe.

7. nutrition:

Nutrition is again a list that contains the nutritious values in the order (calories (#), total fat (PDV), sugar (PDV) , sodium (PDV) , protein (PDV) , saturated fat). Hence each instance will have a list of size 7.

8. n_steps:

Refer to the steps needed for the making of the recipe.

9. steps:

It explicitly mentions the steps in the form of a list. There are n_steps involved in a given recipe then there is a vector of size n_step where each element is in the form of a string.

10. description:

Given in the form of a string is the description of the recipe in brief.

11. ingridients:

Again a list of string where each element present an ingridients required for the recipe.

12. n_ingridients:

Total number of ingridients that goes into the recipe.

From the initial data analysis we inferred that the outliers in the columns n_steps and minutes was high and their distribution was quiet skewed which we had to fix if we decide to keep these columns.

**Feature extraction:**

Given in the form of a list most of the features were not directly usable. Hence we resorted to using binary literals for such features. This gave us with a sparse vecrtor for each instance of the recipe.

Apart from this there were unstructured features like *description* and *name* which were in the form of strings. For such features we first tokenized the string and then applied the tf-idf vectorization. Apart from this we also removed the stop-words to increase the execution efficiency.

**Representing reviews and mapping them with the users:**

Each of the recipe will be rated by some user on the scale of 0-5. If the review given by a user is positive(>3) then the recipe ID associated with that recipe gives us the mapping of the recipe to the user based on the rating.

**Designing the content-based system:**

We have worked individually on two different sets of feature for the system,

1. Item-Item Similarity Based:

Here we have worked with features *minutes ,n_steps, n_ingridients, nutrition vector and the tokenized vector of names*. We got a matrix of size (8607, 485) where each row is an instance of a recipe. Then we have used cosine similarity to find the similarity of the new recipe with other recipes and suggest the top 5 recommendation.

Given approach can be used to suggest similar recipes to the recipe the user is currently reviewing.

2. Query Based:

Here we worked with features *steps, description and ingridients*. We have first converted the string liyerals to a corpus of string having the combined data from each feature simply concatenated. Then we used the tf-idf vectorization the assign proper weights. Then we used cosine similarity to find the similarity between recipes and recommend the top 5.

Such a approach can be useful to suggest the recipe when user uses the search functionality.

**Contributions/Novelty/Insights:**

The insights and novelty for the content based recommendation systems are,

1. This approach is easy to implement and works on memory based architecture.
2. Given the large number of data-points it becomes computationally intensive to work with memory based models.
3. The model will under-perfom if an unknown word is introduced when dealing with the unstructured data.

*Contribution:* The project was executed in the presence of each member being physically available at the time of the execution. Each member provided with his value inputs for a given problem and the best approach was finalized after discussion among all the members.

**Team members :**

1. Ayush Hirdani - 202101139
2. Sumukh Patel - 202101422
3. Takshay Makadia - 202101414
4. Arsh Jindal - 202103021
5. Akshat Prasad - 202101419

