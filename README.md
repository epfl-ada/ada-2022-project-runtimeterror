# Building and analysis of movie arcs

## Abstract
Most plots in the movie business follow one of the well-known story arcs. Like, considering a narrative in which the main character begins in turmoil and finishes in bliss, or in which the main character resides happily but has problems that he/she must overcome before returning to his/her joy. In this project, we aim to explore this phenomenon with the CMU Movie Summary Corpus dataset, in order to identify the most common storylines and how profitable those storylines are. For the purpose of our analysis, we create story arcs by performing sentiment analysis on the plot and  cluster the movies based on the similarities of their story arcs. By taking into account the revenue for each cluster, it will identify the most profitable movie plots. Additonaly, the linked rating dataset of the IMDb platform will add the real life component to the analysis. This study of consumer behaviour could be a real benefit to the movie industry to assure the success of their next production. (165words)

will we add the data over time? (, and the evolution of the most prevalent storyline with time.)? 
(Finally, we can repeat the same procedure but on a list of movie plots taken from different time frames hence resulting in a time series analysis of the evolution of the most prevalent story arcs)

## Research questions
- What is the effect of the presence of emotions on the success of the movie (Do emotional movies have a higher rating IMDB) ? Does the effect differ between genres ?

- What is the effect of the positive/negative emotions on the success of the movie (Do movies that are predominently positive (more than 70% of the lines are positive) have a higher IMDB rating? or is the opposite effect true? and do the observed effect vary per genre ?

- What is the most profitable movie arc per genre, is their a clear winner among the various clusters?

- What is the most rated movie per genre, is their a clear winner among the various clusters?


## Additional datasets
Given that we are interested in the profitability of movie arcs and their linked consumer opinion, we needed a rating system. It has to be based on real assessments but also from reliable sources. For this reason we added in part 2 the title.basics.tsv.gz dataset and title.ratings.tsv.gz from the IMDb platform. 

1. From the basics dataset only the data with the type 'movie' was considered and merged with the ratings dataset over 'tconst', an alphanumeric unique identifier of the title. 

2. With the newly created dataframe, we want to find the average rating. There are some movies with titles in multiple languages, which each have a rating. Therefore, we grouped it by original title and calculated the average rating by multiplying it with the number of votes and sum it.

3. Merging the dataframe of the average rating with each cluster, will provide us the necessary dataframes for the following analysis of our research questions.

### Methods

***Part 1: Getting familiar with the data and constructing the Story Arcs***

**Step 1 and 2: Data scraping, pre-processing and dataset construction.** The dataframe was created form the two datasets provided by CMU Movie Summary Corpus. 

Dataframe: Plot Summary dataset (plots split into sentences + sentiment retieval with VaderSentiment as analyzer) merged with Movie Metadata dataset. Each line in the movie plot is evaluated by the sentiment analyzer as a continous value from -1 to 1 and classified as positive (+1), negative (-1) and neutral (0).

Pre-processing: Drop movies, which do not contain information about the revenue (NaN's in box office) and created 4 different genres (action, adventure, drama and comedy) by subgrouping the given genres.

**Step 2: Create and visualize movie arcs.** Every genre is visualized with a timeline of the average sentiment score to form the story arc.

**Step 3: Clustering** top three movie arcs

***Part 2: From the provided dataset to our sicentific questions*** 

**Step 4: Classifying movies into sentiments.** To analyze the influence of emotion, we first need to separate the movies to each sentiment. Every movie which has more than 70% of either positive, negative or neutral sentiments, is classified inta a positive, negative or neutral movie. This has been repeted for ever genre dataframe and compared to each other.

**Step 5: Creating ratings dataframe.** As explained above in section 'Additional datasets', for each genre, a dataframe with its average rating was created. 


***For Milestone 3:***

**Step 6: Clustering algorithm** We will perform an in-depth analysis on the choice of clustering algorithms and find the optimal number of clusters that will maximize the inter-class variance and minimize the intra-class variance.

**Step 7: Statistical analysis for reasearch questions **

**Step 8: Create data story** get familiar with Jekyll (to build website)

**Step 9: Finalize website, finalize single notebook, update readme (with details of contributions)**


Further details on the proposed data pipelines can be found in the notebook.


### Proposed timeline

Step 1 to 5: **Deadline Milestone 2 18.11.2022**

*02.12.2022: Deadline Homework 2*

Step 6: 09.12.2022

Step 7: 14.12.2022

Step 8: 16.12.2022

Step 9: **Deadline Milestone 3 23.12.2022 **

### Organization within team until P3
Antoine: 

Etienne: 

Melanie:

Yehya:


#### Questions for TA (if any)
