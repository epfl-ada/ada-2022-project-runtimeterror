# Building and analysis of movie arcs

## Abstract
The majority of plots follow one of a few well-known plot arcs in the film industry. Consider a story in which the main character begins in turmoil and ends in happiness, or in which the main character lives blissfully but encounters challenges that must be addressed before returning to his/her delight.
In this research, we propose to investigate this phenomena in order to determine the most popular narratives, how lucrative certain storylines are, and how the most prevalent storyline evolves over time. Examples of well-known story lines include the various Disney movies (i.e., Snow White, Cinderella, Shrek...) where the movie starts with the main character living happily and as the movie progresses, the main character faces difficulties (Snow White eats the apple and faints, Cinderella misses the curfew, Shrek looses his chance of saving the Pheona ...). Accordingly, in order to asses this phenomena, we will first construct the various movie arcs from the movie plots. We propose splitting the movie plots into sentences and performing sentiment analysis on every sentiment. With that, we can generate for every movie present in the CMU Movie Corpus dataset it's corresponding story arcs. Performing such analysis provides us with rich information on the various emotions present in the movies and how such emotions evolves over the course of the movie. With that given, we would like to address the below listed research questions.

## Research questions
The research questions that we would like to answer falls into two domains: (1) Stationary Analysis (2) Time Series Analysis.

In the Stationary Analysis, we would like to answer the following questions:

- 1) What is the effect of the presence of emotions on the success of the movie, Do emotional movies have a higher IMDB rating ? Does the effect differ between genres ? Emotional movies are those in which the bulk of the narrative lines carry either good or negative sentiment and not both at the same time. Non-emotional movies, on the other hand, feature a preponderance of plot lines that are neutral in sentiment.

- 2) What is the effect of the positive/negative emotions on the success of the movie, Do movies that are predominantly positive have a higher IMDB rating? or is the opposite effect true? and does the observed effect vary per genre ?

- 3) What is the most profitable movie arc per genre, is there a clear winner among the various clusters? For example, is the most profitable story arc described in abstract the most profitable, or does the most successful movie arc follow a different trend?

- 4) What is the highest rated movie arc per genre, is their a clear winner among the various clusters?

In the Time Series analysis, we would like to answer the following questions:

- 1) Does the most typical movie arc change over time? If so, what are the various movie arcs that take place in various time periods, and what are their profitability and rating?


## Additional datasets
We required a rating system because we are interested in the financial success of movie arcs and the associated consumer sentiment. It must be founded on accurate evaluations from trustworthy sources. With that we utilized in addition to the CMU Movie Corpus Dataset, the IMDB Dataset. Specifically, we utilized only two files title.basics.tsv and the title.ratings.tsv

1. From the title.basics dataset only the column with the name 'movie' was considered and merged with the title.ratings dataset over 'tconst', an alphanumeric unique identifier of the title. 

### Methods
In order to answer the posed researched questions, we will construct a data analysis pipeline. We divided the Pipeline into 3 major parts as detailed in what follows:  

#### Part 1: Getting familiar with the data and constructing the Story Arcs***

**Step 1: Data scraping, pre-processing and dataset construction.** In this preliminary step, we construct a dataframe from the plot summaries and the movie meta data. We then proceed by tokenizing the plots into sentences and run the sentiment analysis tool (Vader Sentiment Analyzer [1]) on each sentence. With that, we construct two different useful columns (1) Plot scores (2) Plot classifications, where they contain the time series values of the sentences in the plot. The former stores the list of continuous sentiment value ranging from -1 (most negative) to 1 (most positive) while the latter stores the list of discrete sentiment counterparts. 

After that, we perform an exploratory step where we visualize the distribution of the Box Office revenues of various movies and the display number of movies in the CMU Corpus that doesn't have the revenue scores. We also create 4 different dataframes containing the 4 most common genres (action, adventure, drama and comedy). Details in constructing the 4 different genres dataframe is given in the Notebook.

**Step 2: Create and visualize movie arcs.** Now that we have, the different genre dataframes, we visualize a typical movie plot by performing averaging on all the elements of the time series in a way that takes into account that the sentiment time series have different lengths.

**Step 3: Clustering** After visualizing the various most typical movie arcs per genre, we examine the different time series clusters present in each genre. With that, we run a time series clustering algorithm by utilizing the tslearn library [2].

#### Part 2: From the provided dataset to our sicentific questions*** 

**Step 4: Classifying movies into sentiments.** To analyze the influence of emotion on the rating of the movies, we first need to classify the movies to three different classes (negative movie, neutral movie, positive movie). Every movie which has more than 50% of either positive, negative or neutral sentiments, is classified into a positive, negative or neutral movie. This has been repeated for ever genre dataframe and visualized using bar plots.

**Step 5: Creating ratings dataframe.** 
In order to introduce the movie ratings into our analysis, we utilize the IMDB datasets as stated in the additional datasets section. The IMDB dataset contains entries of the movie if all the different languages. Thus in order to have a better estimate of the rating, we grouped the movies by their original title and calculated the rating by taking the weighted average of the different language movie ratings by the number of the votes given to that corresponding movie.

***For Milestone 3:***

**Step 6: Clustering algorithm** In this initial analysis, we utilize the basic TimeSeriesKmeans, yet multiple more powerful clustering algorithms exist such as Kernal K-means. With that, we will perform an in-depth analysis on the choice of clustering algorithms and find the optimal number of clusters using the Silhouette that will maximize the inter-class variance and minimize the intra-class variance.

**Step 7: Provide Detailed Analysis for each research question** Now that we have all the data stored in the various dataframes discussed previously, we will run statistical analysis to quantify weather there exist a heterogeneous relation in the profitability and ratings of different movies arcs in order to answer the stationary analysis questions 1->4. We will then proceed into dividing the dataset into different time frames and visualize the most common dataframes in each time interval and analysis of their profitability and rating.

**Step 8: Create data story** get familiar with Jekyll (to build website)

**Step 9: Finalize website, finalize notebook, update readme**


Further details on the proposed data pipelines can be found in the notebook.


### Proposed timeline

Step 1 to 5: **Deadline Milestone 2 18.11.2022**

*02.12.2022: Deadline Homework 2*

Step 6: 09.12.2022

Step 7: 14.12.2022

Step 8: 16.12.2022

Step 9: **Deadline Milestone 3 23.12.2022**

### Organization within team
Antoine: 

Etienne: 

Melanie:

Yehya:


#### References
[1] Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.

[2] https://tslearn.readthedocs.io/en/stable/
