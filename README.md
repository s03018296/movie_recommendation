# movie_recommendation
## Introduction:
The project code is based on item-based-collaborative filtering. This project's goal was to create a system which was able to recommend new movies to users based on previous movies that other users have positively interacted with. When users are looking for a new movie, we search movie’s they’ve previously rated, and similar movies other users have rated highly. 

## Observation
The dataset that was used consisted of about 9700 movies, 610 users and over a hundred thousand ratings. With this dataset there is also a high sparsity. Out of 9700 movies, only 1700 of them have received at least 10 reviews and out of our 610 users/movie reviewers, only 133 have reviewed at least 200 movies. 

Now the goal of the recommendation system is to only recommend quality movies. This was determined by using only quality user ratings, and to also recommend movies the user has not already seen. To do this the data is filtered so that it only removes users who have not rated at least 200 movies as well as removes movies that have less than 10 user ratings. Based on the pie chart below the majority of the movies and users were deemed “low-quality” by the implemented filters, and thus are removed from the dataset used for recommendations. 

After updating the data with these filters, the sparsity of the dataset is reduced by 23 percent.

## Related Work:

## Methods Used/Solution:

## Data obtained:

## Evaluation:

## Conclusion: 
##### To conclude, after looking over our results, our program runs fairly efficiently and very accurately. We know this due to using the RMSE to test how closely our results were with the expected results of RMSE. In the future, using a larger dataset to train our functions could help lower our RMSE value. The larger dataset would allow our recommendation function to have a wider set of potential answers, allowing for even more accurate predictions. Thank you for watching our presentation and I now open the floor to questions.
