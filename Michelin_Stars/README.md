# Michelin Comes to DC
___

Michelin is not just a industry leader for the manufacturing of tires.  They also produce a guide of the worlds most elite and 
exquisite restaurants.  The Michelin Restaurant Guide was originally created to spur traveling (and using tires), but developed into
one of the most prestigious lists on earth.

Earlier this year Michelin announced that they would be releasing a restaurant guide for Washington D.C.  This created quite a buzz and 
many persons started putting together their list of restaurants they believed would make the cut.  

I participated in the General Assembly Data Science Competition for predicting the Michelin Guide.  My process and Finings are in the 
iPython Notebook.

---
#### Gather
To start this prediction process out I would need two things.  Data by which I could fit my model (restaurants that had been michelin reviewed) and data I could predict with (restaurants in DC).  I started by scraping the [Michelin website](https://www.viamichelin.com) for their information and reviews for all of the restaurants they had given stars or honorable mention in the United Sates.  
- I choice to do only restaurants the US to prevent the influence of culture gaps or continental grading criteria.  There is the equivalent of a food truck in Asia with a Michelin star.
- Scraping honorable mentions was important in bring in training data that would allow the model to develop the binary distinguishment of 'Star(s)' or 'No Star(s)'
- Prior to this guide only the cities of [New York](https://www.viamichelin.com/web/Restaurants?address=New%20York),[Chicago](https://www.viamichelin.com/web/Restaurants/Restaurants-Chicago-_-Illinois-United_States) and [San Francisco](https://www.viamichelin.com/web/Restaurants?address=San%20Francisco%20CA) had active Michelin Guides.  (Las Vegas used to have a Michelin guide)
Using the Michelin website I could get information or restaurants like their rating, price, location, name and a brief _professional_ review.  

To get data to predict on I could have used Yelp or Google Reviews, but for times sake I found a list put out by the Washintonian of their [100 Best restaurants in DC for 2016](https://www.washingtonian.com/2016/02/08/100-very-best-restaurants/2016/) and scraped that.  What was nice about this was their information format was similar to that of Michelin's in that the had price ranges and a brief _professional_ review as well.

---
#### Data Prep
A little data massaging was needed to convert categorical features into values processable by a model.
- Text Vectorization of reviews (TFIDF)
- Dummy variables for cuisine type
- Price converting to a simpler scale, 1-5, instead of USD ranges.
As I collected the data I could easily clean and format it by my means when I gathered it.

---
#### Model
I experimented with a could classification models..
- Random Forest, this was not used as a predictor but as a means of feature selection using the extra trees feature importance.  I got the 250 most important features, which now that I look back on it, TFIDF would create features that are really important for a single observation.  Not the smartest move.  Anyways, these 250 most important features were used for the rest of the models.
- Logistic Regression/Classification, more or less my default exploratory model which I use to evaluate the performance of others as it basically trys to simulate if the observation 'Has It' or does not.
- K Nearest Neighbors, why not see what the other 5,7 or 13 most likely restaunts are as far as Michelin reviews?
- Support Vector Machine Support Vector Classifier, figure out those vectors that best separate classes and use those as means to divide the data.  

The competition had a unique criteria for scoring that caused me to assess models differently and have to create my own scoring means for evaluating a model. Basically, predictions that were 1 star value off (except 0-1) were not completely incorrect in my mind.

At this point I selected the KNN model with 7 neighbors as the model that I wanted to try to optimize.  Spun up a AWS compute instance and used it to run a GridSearch CV.

---
#### Conclusion
My final Predictions were Fiola Mare, Masseria, Fiola, Preserve, Obelisk, Del Campo, Woodberry Kitchen and Centrolina.  All of which would be awarded one star.  

Out of the 12 Restaurants that recieve Michelin Stars, only 8 were actually in my modelling data.  
_(Minibar, Blue Duck Tavern, The Dabney, Fiola, Masseria, Plume, The Inn at Little Washington, Rose's Luxury)_

With my final model I predicted 2 of the possible 8 I could have gotten.  
_(Fiola, Masseria)_

If i went with my original Logistic Regression I would have got 4 of 12 right.   
_(Plume, The Inn at Little Washington, Blue Duck Tavern, Minibar)_

Different models came to different conclussions of correct information.  In the future when faced with a similar project I am definitely going to incorporate an element of multiple model aggregation, such as a voting classifier.

In the end my models always did one thing correct and that was never predicting any restaurant in DC would get 3 stars.
