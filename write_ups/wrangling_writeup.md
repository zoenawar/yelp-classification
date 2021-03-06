
After the data was injested into the Mongo database, we had to wrangle the data into a subset for our model.

The problem to solve now was two fold : filter out reviews that would not help our model, find users with enough reviews that we could both train models on thier reviews and have a meaningful set of reviews to test those models on, and prepare the data so that it would be in a form that could be fed thorugh the model.

The academnic dataset provided by Yelp consisted of 5 json files : Business.json, Users.json,Reviews.json, checkins.json and tips.json. For our project we did not use the Checkins or Tips dataset.

The Business dataset had a json dictionary for representing each business in the dataset and information about the business type, general information such as thier business hours and information about how many reviews and the aggregate rating of the business.

The Reviews dataset had all a json dictionary for each review, the user id of the author of that review, the business id of the businsess that was being reviewed, the rating for that review, and the number of cool, useful or funny compliments, and data of the review. 

The User dataset had a json dictionary for each user in the data set, with summary information such as the number of places they had reviewed, the number of checkins, and the number of compliments they had gotten. 

As the reviews of a user and the reviews of restaurants are what drive our recommendation system, we had to subset the yelp reviews to filter in only reviews that were about restarantes. Also, we had to find users that had enough reviews about restaurantes that there would be enough reviews to train a model on to make meaningful recommendations but also enough reviews that we could subset a testing set from their reviews to check performance of that model. 

We had to create a set of yelp reviews that were of restarauntes and from users that had at least 100 restuarnte reviews on yelp. 

The business data set has a business id and the type of business. We created a list of business ids that were for restaurnate businesses. 

We then used to loop through all of the reviews and create a new list of reviews that had business ids in our restaurant business id list.

We then used the user data set to select user ids for users  that have more than 100 reviews, and used that list of user ids to subset the data set of restaurante reviews.

However just because a user has over 100 reviews doesn't mean that they have over 100 restaurante reviews, so we then counted the number of reviews each user had in our list of restaurante reviews that had users that had more than 100 total reviews to see how many restaurant reviews they had.

Once we did that, we had a list of 228 users that had over 100 restaurant reviews. We created a dictionary where the key was the userid and the value is a list of all of their reviews. 

