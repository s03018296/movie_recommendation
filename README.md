# movie_recommendation
## Contributers
Pak Hei Lam
Ethan Coulter
Maxim Kasianiuk
Kevin Man
Joseph Power
Hayden Jeanson

## Introduction:
The project code is based on item-based-collaborative filtering. This project's goal was to create a system which was able to recommend new movies to users based on previous movies that other users have positively interacted with. When users are looking for a new movie, we search movie’s they’ve previously rated, and similar movies other users have rated highly. 

## Observation
The dataset that was used consisted of about 9700 movies, 610 users and over a hundred thousand ratings. With this dataset there is also a high sparsity. Out of 9700 movies, only 1700 of them have received at least 10 reviews and out of our 610 users/movie reviewers, only 133 have reviewed at least 200 movies. 

Now the goal of the recommendation system is to only recommend quality movies. This was determined by using only quality user ratings, and to also recommend movies the user has not already seen. To do this the data is filtered so that it only removes users who have not rated at least 200 movies as well as removes movies that have less than 10 user ratings. Based on the pie chart below the majority of the movies and users were deemed “low-quality” by the implemented filters, and thus are removed from the dataset used for recommendations. 

![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/pie1.jpg)
![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/pie2.jpg)

After updating the data with these filters, the sparsity of the dataset is reduced by 23 percent.

## Related Work:
The reason why our SVD function is different from the standard one is because we have also implemented a GridSearchCV in order to tune the SVD algorithm parameters. GridSearchCV allows us to find out the parameter combination that yields the best results for the hyper-parameters in our algorithm. We are going to tune the learning rate(lr_all) and number of epochs(n_epochs). 

The implementation of the SVD function performed very closely, and in some cases better than many other types of filtering methods. Some of the baseline tests we compared it to are SVDpp, KNN, KNNbasic, and many more. This let us know that our implementation could compete with other filtering algorithms for time, and accuracy. 
## Methods Used/Solution:
With item-based collaborative filtering being implemented into the project, which is a recommendation technique that analyzes the similarity between items using the ratings given by users. This uses the Similarity function as shown below. 

![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/similarity.jpg)

What the similarity function does is it takes two movies and calculates the similarity, and how they compare with one another based on the likeness of users. First, numerous ratings are taken of both movies and then the sum of the results is produced. It will assign this value to the variable x. Second, the square of one movie’s ratings is taken, then summed, followed by taking the square root to get a final value. This process then proceeds with another movie. Both values that were calculated will then be multiplied with one another. This will  produce the y value. Third, dividing both x and y values which then gives a score that indicates how similar movies 1 and 2 are. The cosine similarity equation that is being used to check on the ratings for the items then produces a matrix that shows how similar the movies are with one another. 

![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/movieID_matrix.jpg)

As you can see the similarity scores between all the movies the higher the score the more similar they are with one another. Knowing which movies are now similar with one another, the task now is to find the right movies to recommend to users based on the matrix created. Having this, the program will combine the similarity matrix with the user’s past history of ratings in order to generate a recommendation. 

![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/score.jpg)

Based on the equation above here’s what the following represents:
●	u is the UserId for which we’re generating a recommendation for
●	 i is the movie that’s being considered as to either recommend it or not. 
●	Score (u,i) will create a score that shows the strength level of the recommendation of movie ‘i’ to the user.  
●	j will be the movies similar to the main movie. 
With the equation performing this it’ll produce us another matrix of scores that’ll recommend the best movies. 

## Data obtained:
Test case1: User 1 has given a 5.0 rating to Rear Window, The Shawshank Redemption, Battle Royale and so on. This information was crucial in being able to predict recommended movies for this user. These 5 star ratings are used to find out what movies user 1 likes in particular. After gathering this information, we are then able to move on to the prediction. The resulting recommendations do not contain any of the highly rated movies since user 1 has already seen them. Since previously rated movies have been removed from the pool of recommendations we are left with the top recommended movies for specifically user 1. Each movie was assigned a score value which made it easy to rank the movies. This is calculated by using our score equation/algorithm explained earlier above. Presented below are 2 test results of our algorithm, the first one being user 1 and the second being user 10. 

![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/result1.jpg)
![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/result10.jpg)

After testing our program rigorously, we have found that our program is fairly reliable in predicting movies that would correspond to the users personal ratings. We know this due to testing multiple different users and checking the recommendation value used to rank our movies, while doing this our program would choose the highest value of correlation for each movie a majority of the time. We found that every so often a movie that had a lower recommendation score would be one or two higher on the top 10 recommended than it should have been.

## Evaluation:
After researching many methods of evaluating outcome, we decided that RMSE would be the best means of evaluating. RMSE is used in real world applications in predicting outcomes, and accuracy of the outcomes, which is why we decided it would fit our project perfectly.  The outcome of using RMSE would predict how close our ranking was to the expected value from RMSE, while also providing a value that ranked the accuracy. For example, when User 3 wants movies suggested, after creating the matrix full of ratings for our recommender to choose from, movie ID 113 was rated a (3.5) from our predictions matrix. When comparing it to the RMSE value, RMSE predicted it should have been (3.67), which is a mis accuracy of approximately .48% which is relatively low. This shows us that our method works to a high degree of accuracy, while also having a very low runtime of O(N).
To prove that our SVD algorithm is relatively efficient compared to other algorithms, we have concluded a benchmark below with the RMSE scores of other algorithms and compared it with our algorithm. From the 2 tables above, our test case 1 gave out a RMSE of 0.8137 and test case 2 gave out a RMSE of 0.8150, both of them have a low test RMSE than all the algorithms’ in the benchmark, just slightly larger than SVDpp’s algorithm (however, this algorithm has an extremely large fit and test time). Overall, our algorithm is proven to be well-performed in terms of efficiency.

![alt text](https://github.com/s03018296/movie_recommendation/blob/a1cc33710ea28ece778939b7fb7dfe24e8f64a50/images/test_rmse.jpg)

## Conclusion: 
To conclude, after looking over our results, our program runs fairly efficiently and very accurately. We know this due to using the RMSE to test how closely our results were with the expected results of RMSE. In the future, using a larger dataset to train our functions could help lower our RMSE value. The larger dataset would allow our recommendation function to have a wider set of potential answers, allowing for even more accurate predictions. Thank you for watching our presentation and I now open the floor to questions.
