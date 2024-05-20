# Intelligent_Information_Retrieval_RecommederSystems
Recommender System using Embeddings

created embeddings for users and businesses from the review dataset, and use them to predict the star rating of a given business for a given user.
Involved two steps:

Step 1: Using the training dataset "reviews_train.csv", constructed embedding tables/databases for users and businesses (one table/database each). 
Step 2: Using the embeddings, for each user-business pair in the test dataset "reviews_test_all.csv",  predicted the star rating.  Then  measure the accuracy of your predictions.

**Create Embeddings:**
Created embeddings tables/datasets for users and businesses (i.e,. a user embedding table and a business embedding table).  Each table is keyed by id's (user_id or business_id), and the values are embeddings of each user/business.
To create an embedding for each user/business,  first tokenize the combined string (or list of strings)  (*).  Then  look up the embedding of each token in the string from a lexical embedding resource and create a mean vector as the embedding of the user/business.

**Recommendations (Rating Predictions)**
For each user-business pair in the test dataset ("reviews_test_all.csv"), used the two embeddings tables to predict a star rating score -- the score that the particular user would give to the particular business.
By using embeddings, we can obtain the preadicted score by simply computing the dot product between the user embedding vector and the business embedding vector.
Then  compute the error of the prediction -- a squared difference between the prediction and the ground truth (the 'stars' column in the test dataset ).
Finally reported the RMSE error over the entire test dataset.

**Item-based Collaborative Recommendation using Embeddings**
since the recommendations will be based on the embeddings, queries that simply ask for "top" or "best" businesses are not suited for this task.
Instead, queries that ask for 'similar' to a particular business would be good.
For example,
 "List five restaurants that are similar to 'Pai Northern Thai Kitchen' in Toronto" -- fOR THIS we  identify restaurants in toronto from the original businesses table.  Then  compare each of their embeddings (by looking up in the business embeddings) against the embedding of  'Pai Northern Thai Kitchen'.  Select the top five similar restaurants and displayed their name, stars and categories.
