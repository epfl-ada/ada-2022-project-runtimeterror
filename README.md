# Building and analysis of movie arcs

## Abstract
Most plots in the movie business follow one of the well-known story arcs. Like, considering a narrative in which the main character begins in turmoil and finishes in bliss, or in which the main character resides happily but has problems that he/she must overcome before returning to his/her joy. In this project, we aim to explore this phenomenon with the CMU Movie Summary Corpus dataset, in order to identify the most common storylines and how profitable those storylines are.(, and the evolution of the most prevalent storyline with time.)?  For the purpose of our analysis, we create story arcs by performing sentiment analysis on the plot and  cluster the movies based on the similarities of their story arcs. By taking into account the revenue for each cluster, it will identify the most profitable movie plots. Additonaly, the linked rating dataset of the IMDb platform will add the real life component to the analysis. This study of consumer behaviour could be a real benefit to the movie industry to assure the success of their next production. (165words)
(Finally, we can repeat the same procedure but on a list of movie plots taken from different time frames hence resulting in a time series analysis of the evolution of the most prevalent story arcs)

## Research questions
- What is the effect of the presence of emotions on the success of the movie (Do emotional movies have a higher rating IMDB) ? Does the effect differ between genres ?

- What is the effect of the positive/negative emotions on the success of the movie (Do movies that are predominently positive (more than 70% of the lines are positive) have a higher IMDB rating? or is the opposite effect true? and do the observed effect vary per genre ?

- What is the most profitable movie arc per genre, is their a clear winner among the various clusters?

- What is the most rated movie per genre, is their a clear winner among the various clusters?


## Additional datasets
Given that we are interested in the profitability of movie arcs and their linked consumer opinion, we needed a rating system. It needs to be based on real assessments but also from reliable sources. For this reason we added the title.basics.tsv.gz dataset and title.ratings.tsv.gz of the IMDb platform. 

1. how merged etc on which id's
2. etc 

### Methods

***Part 1: Getting familiar with the data and constructing the Story Arcs***
**Step 1: Data scraping, pre-processing and dataset construction.** The dataframe was created form the two datasets provided by CMU Movie Summary Corpus.

Dataframe: Plot Summary dataset (plots split into sentences + sentiment retieval with VaderSentiment as analyzer) merged with Movie Metadata dataset

Pre-processing: Drop movies, which do not contain information about the revenue (NaN's in box office), create 4 different genres (subgrouping the given genres)

**Step 2: Create and visualize movie arcs**
**Step 3: Clustering** 

***Part 2: From the provided dataset to our sicentific questions***
**Step 4: Classify movies into sentiments**
**Step 5: Create ratings dataframe**

**Step 6: **


Further details on the proposed data pipelines can be found in the notebook.

Split into Part one and two
Part one: mainly getting familiar with the data and constructing story arcs. For this the plot summaries have been read into as id and plot of each movie. Plot split into sentences as array. Build sentiment analyzer with vader sentiment as sentiment instensity analyzer, which gives back a continuous sentiment score. Additionally this score has been classified into positive (1), neutral (0) and negative (-1) scores. To add more information in the dataframe, the plot summaries with the sentiment scores were merged with the movie metadata dataset, which added the release date, title, box office sales, production country and genre. Because we are interested in the revenue depending on the movie genre, the new dataset has been processed by removing all movies without revenue values. (reduced dataset to a sixth of the initial)
The next step it so split the data into their genres. all genres are sectioned in the four most common genres: adventure, action, drama and comedy. (do need to add which genres in which main genre?)
columns = zip_longest(*list_values, fillvalue=0) what does * mean?

For every main genre, the most common movie arc was retrieved, by taking the average of all datapoints? And plotting them. In addition, all four genres were clustered depending on their movie arc in three clusters. How? What is 
gak_km = KernelKMeans(n_clusters=3, kernel="gak")


To further analyze our data, the second part processed the data to undertake different comparisons. Here, each movie was divided into either a positive movie, negative movie or neutral movie, depending on the sentiment plot classification. The movie is classified in to a positive movie if 70% percent of the overall sentiment scores are positive scores (+1). Same approach was used for the negative movies. The rest is classified as a neutral movie.

An additional data set was used, the ratings from ???, where only the data regarding movies was used (no other category). It contains the average rating, its number of votes and the title. 
??? -> was it later merged with the other df like the movie plots etc?


With that, we can find the mean and variance of the revenue for each cluster, eventually leading to the identification of story arcs of the most profitable movie plots. Finally, we can repeat the same procedure but on a list of movie plots taken from different time frames hence resulting in a time series analysis of the evolution of the most prevalent story arcs.



### Proposed timeline
For the final milestone, you will be expected to execute your project proposal and describe your project in a data story. Data stories are a blog post or short article, with an important visual component, using data to tell a story and illustrate it effectively. You can be less formal here (although methods and math should then appear in the notebook), but more visual.


Step 1:
Step 2:
Step 3:
Step 4:
Step 5:

By 09.12.2022: get familiar with Jekyll (to build website)
By 16.12.2022: statisitical analysis
Deadline P3 submission: 23.12.2022 finalize website, finalize single notebook, update readme (with details of contributions)


### Organization within team until P3
Antoine: 
Etienne: 
Melanie:
Yehya:


#### Questions for TA (if any)
