# A Recipe for a perfect story!
## Datastory 
Uncover the secret to creating the perfect recipe for a cinematic masterpiece! Follow the link to our datastory and discover the ingredients for success: [Datastory](https://melbrt.github.io/runtimeterror_ds/ "datastory") 

## Abstract
In this study, we propose to investigate the prevalence and evolution of popular plot arcs in the film industry. Examples of well-known storylines include those found in Disney movies, such as Snow White, Cinderella, and Shrek, where the main character starts off happily and faces challenges as the movie progresses and concludes with happily ever after! Through the use of sentiment analysis on the movie plots in the CMU Movie Corpus dataset, we aim to identify the most popular storylines and assess their commercial success. We will also analyze the emotional journey of the characters in these films to understand how these storylines evolve over time. Our research aims to provide valuable insights into the factors that contribute to the success of a film.

## Research questions
The research questions that we would like to answer falls into two domains: (1) Stationary Analysis (2) Time Series Analysis.

In the Stationary Analysis, we would like to answer the following questions:

* What is the effect of the presence of emotions on the success of the movie, do emotional movies have a higher IMDB rating? Does the effect differ between genres?

* What is the effect of the positive/negative emotions on the success of the movie, do movies that are predominently positive (more than 50% of the lines are positive) have a higher IMDB rating? or is the opposite effect true? and do the observed effect vary per genre? 

* What is the most rated movie arc per genre, is there a clear winner among the various clusters?

In the Time Series analysis, we would like to answer the following questions:

* What is the most profitable movie arc per genre, is there a clear winner among the various clusters? Did the profitability change over time?


## Additional datasets
We required a rating system because we are interested in the financial success of movie arcs and the associated consumer sentiment. It must be founded on accurate evaluations from trustworthy sources. With that we utilized in addition to the CMU Movie Corpus Dataset, the IMDB Dataset. Specifically, we utilized only two files title.basics.tsv and the title.ratings.tsv

1. From the title.basics dataset only the column with the name 'movie' was considered and merged with the title.ratings dataset over 'tconst', an alphanumeric unique identifier of the title. 

### Methods
In order to answer the posed researched questions, we will construct a data analysis pipeline. We divided the pipeline into 3 major parts as detailed in what follows:  

#### Part 1: Getting familiar with the data and constructing the Story Arcs

**Step 1: Data scraping, pre-processing and dataset construction** In this preliminary step, we construct a dataframe from the plot summaries and the movie meta data. We then proceed by tokenizing the plots into sentences and run the sentiment analysis tool (Vader Sentiment Analyzer [1]) on each sentence. With that, we construct two different useful columns (1) Plot scores (2) Plot classifications, where they contain the time series values of the sentences in the plot. The former stores the list of continuous sentiment value ranging from -1 (most negative) to 1 (most positive) while the latter stores the list of discrete sentiment counterparts. 

After that, we perform an pre-processing step where we visualize the distribution of the Box Office revenues of various movies and the display number of movies in the CMU Corpus that doesn't have the revenue scores. We also filter out all the movies that have less than 5 sentances in their plot. In addition to that, we create 4 different dataframes containing the 4 most common genres (action, horror, drama and comedy). Details in constructing the 4 different genres dataframe is given in the Notebook.

**Step 2: Create and visualize movie arcs** Now that we have, the different genre dataframes, we visualize a typical movie plot by both (1) randomly choosing different movies in different genres (2) performing averaging on all the elements of the time series in a way that takes into account that the sentiment time series have different lengths.

**Step 3: Clustering** After visualizing the various most typical movie arcs per genre, we examine the different time series clusters present in each genre. With that, we run a time series clustering algorithm by utilizing the tslearn library [2].

#### Part 2: From the provided dataset to our sicentific questions

**Step 4: Classifying movies into sentiments** To analyze the influence of emotion on the rating of the movies, we first need to classify the movies into three different classes (negative movie, neutral movie, positive movie). Every movie which have more than 50% of either positive, negative or neutral sentiments, is classified into a positive, negative or neutral movie. This has been repeated for ever genre dataframe and visualized using bar plots.

**Step 5: Creating ratings dataframe** 
In order to introduce the movie ratings into our analysis, we utilize the IMDB datasets as stated in the additional datasets section. The IMDB dataset may contain entries of the same movie in the different languages. Thus in order to have a better estimate of the rating, we grouped the movies by their original title and calculated the rating by taking the weighted average of the different language movie ratings by the number of the votes given to that corresponding movie.


#### Part 3: Analysis and answering the sicentific questions

**Step 6: Clustering algorithm** We used the tslearn library to cluster the emotional arcs of movies by genre using two different representations of time series data (continuous and discrete) and the Silhouette score to evaluate the quality of the clusters and choose the optimal number of clusters. With that, we performed an in-depth analysis in order to find (1) The best features (discrete/continuous) that results in the most reasonable clustering (no similar clusertoids) (2) the optimal number of clusters using the Silhouette score that will maximize the inter-class variance and minimize the intra-class variance.

**Step 7: Provide detailed analysis for each research question** Now that we have all the data stored in the various dataframes discussed previously, we run statistical analysis to quantify weather there exist a heterogeneous relation in the profitability and ratings of different movies arcs in order to answer the stationary analysis questions 1->4. We then proceed into dividing the dataset into different time frames and visualize the most common dataframes in each time interval and analysis of their profitability and rating.

**Step 8: Create data story** In order to present our findings, we created a datastory using Jekyll.

### Executed timeline

Step 1 to 5: **Deadline Milestone 2 18.11.2022**

*02.12.2022: Deadline Homework 2*

Step 6: 09.12.2022

Step 7: 14.12.2022

Step 8: 16.12.2022

Step 9: **Deadline Milestone 3 23.12.2022**

### Organization within team

<table class="tg" style="table-layout: fixed; width: 342px">
<colgroup>
<col style="width: 16px">
<col style="width: 180px">
</colgroup>
<thead>
  <tr>
    <th class="tg-0lax">Teammate</th>
    <th class="tg-0lax">Contributions</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Yehya </td>
    <td class="tg-0lax"> (1) Worked on the pre-proccessing the data by executing step 1, step 2 in the method section. <br> (2) Worked on classifying the movies into different emotional classes by executing step 4.<br> (3) Constructed an matched study to nullify the effect of hidden confounds in the analysis by executing step 7.<br> (4) Analyzed and ran statistical tests on the effect of emotions on the movies by executing step 7.<br> (5) Contributed to the Datastory </td>
  </tr>
  <tr>
    <td class="tg-0lax">Antoine </td>
    <td class="tg-0lax"> (1) Worked on constructing the various story arcs present by executing step 3. <br> (2) Worked on analyzing the clustering, plotting the silhoutte scores by executing step 6<br> (3) Worked on running statistical tests to answer the questions 3, 4 and 5 by executing step 7<br> (4) Worked on visualizing the various findings through bar plots and timeseries plots. </td>
  </tr>
  <tr>
    <td class="tg-0lax">Etienne</td>
    <td class="tg-0lax"> (1) Worked on constructing the various story arcs present by executing step 3. <br> (2) Worked on constructing the ratings dataframe and joining it with the CMU Dataset by executing step 5<br> (3) Worked on running statistical tests to answer the questions 3, 4 and 5 by executing step 7<br> (4) Worked on visualizing the various findings through bar plots and timeseries plots. </td>
  </tr>
  <tr>
    <td class="tg-0lax">Melanie:</td>
    <td class="tg-0lax"> (1) Worked on analyzing the ratings and constructing the various plots present in the Datastory. <br> (2) Worked on analyzing the findings and provide prominent explanations. <br> (3) Worked on validating the algorithms developed by running tests. <br> (4) Documenting the readme and other aspects of the notebook. 
  </tr>
</tbody>
</table>



#### References
[1] Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.

[2] https://tslearn.readthedocs.io/en/stable/
