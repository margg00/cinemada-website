---
layout: default
---

# The Actor's Playbook: A Guide to Picking Roles for Hollywood Success

Are you an aspiring Hollywood actor? Have you ever wondered durign a casting if this role was truly meant for you? If so, you have come to the right place. For every actor, the path to success is paved with strategic choices. Every role you choose might launch your career or derail it completely. It becomes hence crucial to understand the effect of succession of roles on Hollywood actors success.
In this guide, we will explore the importance of role types (lead or secondary or essemble role) and how each can shape your future as an actor. Based on movie plot summaries and scripts, we will also uncover the significance of dialogues and screen time. The budget and financial scale of the movie projects are also aspects we will delve into.

So whether you're about to attend your first audition or looking to recalibrate your career trajectory as an actor, join us in our exploration.



## Get to know our data

To perform this analysis, a combination of different datasets were used, the first being the CMU Movie Summary Corpus. It consists of a collection of 42,306 movie plot summaries extracted from Wikipedia, a medatada of 81,741 movies and 450,669 character/actor duos extracted from Freebase. 
This data was merged with an additional movie and actor dataset from Tmdb website, providing supplementary information such as the movies budget, genres, vote count and vote average as well as movie and actor popularity. 

- filtered our data to keep only Hollywood
- filtered actors to remove ones who have ended their career a long time ago
- 

## How to measure an actor success?

An actor success is a tricky metric to discover, considering the amount of variables that can influence it. 
The popularity of an actor as computed by TmdB fluctuates in time and is impacted by the number of views for the day as well as the previous day score. If we look at the metric sampled recently and plot it against the release date of an actor most recent movie, it is clear that more recent movies produce more popular actors. 



This can be related to the effect of trend. In fact, one can observe a huge peak in TmdB movie popularity in the very recent months.



To mitigate the effect of trend, the actor popularity metric was normalized using a "within group" z-score normailzation. Each actor score is relative to the mean and standard deviation of the scores of actors whose most recent movie was released in the same year range.

To compliment this time fluctuating indicator, a second actor popularity metric was added, published by YouGov. They provide nationally representative popularity scores.They define the fame of the 15000 most popular American actors, as the percentage of people in the United States who have heard of a them. According to the Pew Research Center, their methodology "consistently outperformed" other online polling companies.  
Since this measurement only applies to 1500 actors out of the ??? actors in our filtered database, we chose to use Support Vector Machines to predict the fame of the remaining actors, based on several features such as ???

Define the features (Yasmin)

### Add plot that shows the importance of features in predicting the fame

Explain which features best explain the fame metric. We want to analyze them (budget)

A part from the popularity indicators, an actor success can also be defined as the number of awards he or she has received. And what more prestigious than an Oscar? Since 1929, Oscars have been recognizing excellence in cinematic achievements. We retrieved the nomination and awards winnings data from the Oscars for each actor in our dataset. 

- Golden Globe award
- Critic's Choice award
Explain principle of those awards
added weight of 2 for the best actor and for the wins of oscars


Final metric add forumula
(weighted sum or different metric  awards and popularity)
Explain how fame and popularity balance each other
Added different weight on each factor based on their perceived importance. 
Explain higher weight for awards because sucess gap between no award and 1 award should be greater than between 1 and 2 awards

### Add other awards (Golden Globes Awards, Critics' Choice Awards)?

### Add plot that shows new popularity
### Add complete formula for the success metric


## How to represent the timeline of an actor's career ?

Our popularity score was computed partly based on scores sampled recently. It is a representation of the cumulative success throughout an actor career. Our goal is to understand how each role he played or the combination of those roles may have impacted this score. In fact, each career trajectory and the distribution of role features is unique for each actor. As a result, it would be poor choice to solely base our analysis on the average of those features, such as the average genre, average movie budget or average role importance. Instead, we need to consider the evolving of those features in time to truly understand their impact on success. For this reason, we decide to divide the career of actors based on the number of movies they played. 


define time ranges
3 datasets 

## What type of roles should you pick?
 
Depending on your experience as an actor, you might not be offered lead roles in big production studio movies right away. However, to build up to that point, the choice of the type of role can greatly impact your future success. 
To answer this question, we first 

gold data = plots + scripts 709 movies, 11668 characters (from filtered dataset 10k movies)
eval set 94 / 792
test set 94/791

- distribution of actor popularity based on different percentage ranges of the script dedicated to a role
- hypothesis testing
- prediction:(GradientBoostingRegressor) predict popularity based on original features (age, genre, ethnicity, most recent release date,  Genres, production studio  ), then predict popularity based on those features + role importance (percentage of script)
    - reduce the effect of confounding variables



## What role plays the budget of movies in actor success ?

Are high budget movies necessarly producing more popular actor? That's a question that should be answered. 
First let us have a look at the distribution of our popularity metric bashed on the cumulative budget of the movie they played in.

- plot dis of pop based on movie budget
- correlatation analysis as above
- regression analysis: Popularity=β0 +β1×Budget+β2×Importance+β3×(Budget×Importance)
- separate 2 groups: one hot encoding of role importance (low percentage, high percentage)



analysis part on 5000 actors (hollywood filtering or lack of info on known movies in database)


define trajectory => define time periods in trajectory (beginning, middle, end)

### Is it best to divide in 3 groups for every actors or in N groups, N depending on the number of movies

avg pop, avg rev, avg, 


frq of movie, age beginning career, 
divide number of movies 3 ranges with same n movies
add features used for the regression of fame. Train using SVM, how features are correlated. polynomial kernel, trained on (80% test on 20% of 1500) then train on all 1500, predict for others
We see that budget at beginning hot feature
Number of movie high impact
only use actors with high number of movies
if use separation of trajectory, all actors seem to be at the end
look at time span between last and first movie
divide based on equal time: 20, 40, rest

3 for fame for SVM prediction: one for actors in beginning
                       one for actors in middle
                        one for actor in end

awards: sum them all, more weights for wins (*2) and more weights for best actor(*2)


- reduce number of movies: remove movies where all (or N) actors have finished their career (last movie release date was more then 20 years ago) 
- create 3 different datasets
- try 3 different SVMS on 3 datasets
- merge dataset back again
- define popularity metric (success= fame + awards + popularity tmdb )
- have final dataset: 
  age beginning, 
  avg_genre for 3 time periods,
  gender,
  progress in career (are there in the beginning, middle or end portion? )
  avg_role_importance (avg_tmdb order for now) for 3 time periods,
  std_role_importance
  avg_budget for 3 time periods
  std_budget for 3 time periods
  our success metric
  production studio for majority of movies in 3 time periods 






df: 

age beginning movie, time in career, tmdb order, 

normalize features first

explain balance fame + popularity: one best but extracted by hand, one time dependent but more reliable

order: strong precision, low recall

clip high order actors for now 