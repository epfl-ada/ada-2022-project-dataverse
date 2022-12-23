# The seventh art under investigation

## The Link to our DataStory

https://delta3361.wixsite.com/dataverseteam

## Table of Contents
- [Abstract](#abstract)
- [Research Questions](#research-questions)
- [Additional datasets](#additional-datasets)
- [Methods](#methods)
- [Proposed timeline](#proposed-timeline)
- [Organization within the team](#organization-within-the-team)
- [Navigating the repo](#navigating-the-repo)


## Abstract
The global film industry was worth $136 billion in 2018. The top three film-producing countries are the United States, India and China. However, despite its supposed diversity, there are common patterns and characteristics in movies which we aim to investigate. Our project is mainly to explore the characteristics of most appreciated movies. Therefore, the review score of a film will be our main variable of interest. For this aim, after exploring the main topics by genre for each country, we will investigate if the review scores could be predicted by the titles or more broadly by our enriched data. Finally, we will try to verify if movies based on books are more appreciated than those that are not based on books and to explore empirically the popular belief which states that movies based on books are less appreciated than their book counterparts.   


## Research Questions

Q1. What is our data and how are the movies connected to books?

Q2. Can we predict the movie review score based on our data ?

Q3. What are the most representative words in movies and book-based movies ? 

Q4. Do movies are less appreciated than their books counterparts?    

## Additional datasets
- Wikidata
 
  - We extract the information from Wikidata using SPARQL queries and merge it with the original CMU dataset using Freebase IDs. We extract data on movie reviews, constraining reviews to be from Rotten Tomatoes by averaging the scores for fairness. We also extract the point in time the scores were collected. There are 17491 rows in total. The SPARQL query for replication of the results is provided in the notebook.
  - We extract information on nationalities to match a nationality Freebase ID in the original dataset with the nationality.
  - We extract the data on films that received any of the  Academy Awards. There are 1546 rows in total.
  - We extract the data on books that served as a base for films. There are 7017 rows in total.
  - We extract pairs (IMDb ID, Freebase ID) to match the subtitles dataset with CMU dataset. There are 102807 rows in total.
  
- Books ratings

  - We will first lower case and remove punctuation from the titles and then merge the dataset through the title name from the list ”data based on books” from the wikidata (7’017) for both of the datasets below. The scores of both dataset will be normalized as the scales are not the same. Therefore, books ratings that are available in both datasets will be averaged. 

  - https://github.com/luminati-io/Amazon-popular-books-dataset/blob/main/Amazon_popular_books_dataset.csv. Rating, title, best sellers rank variables will be used for the analysis, which has 2’269 entries.

  
- Subtitles
  - This dataset is processed in the `Subtitles` section
  Dataset is available at the following link: https://www.kaggle.com/datasets/adiamaan/movie-subtitle-dataset?select=movies_meta.csv
  - It stores several thousand movies with metadata and subtitles.
  The `movies_meta.csv` table contains movie metadata and `imdb_id`.
  The table `movies_subtitles.csv` stores subtitles of movies for different time periods and also stores `imdb_id`.
  - We merge this dataset with our original dataset by columns `imdb_id` and `freebase_id`
  (With `Wikidata` dataset we got a `merge_ids` table (file `merge_ids.csv` in Subtitles folder) that stores both `imdb_id` and `freebase_id`. Through this table we merge the datasets).
  - After merging we have about 3000 movies in our original dataset for which we now have a list of subtitles






## Methods

Q1. To look for trends, we can analyze the amount of films produced in a period along with box revenue and review scores (but the two latter ones have limitations). We will find countries that are leading the industry. 
We analyze the overall data for different genres and countries. We apply statistical analysis to answer questions like “Do films based on books have higher review score?” and find dependencies that relate to review score. 

Q2. We want to track the evolution of the most descriptive and common words in films during time and see how these characteristics vary across different film categories. The plan is to perform a linguistic analysis on subtitles and plot summaries using TF-IDF and find the most representative words. We will cluster films based on their genre, country, time of creation, runtime and other features and check out how these words vary across different clusters.

Q3. We plan to predict the review score by training the MLP on the regression problem. We will use our data in such a way that text variables (for example, summaries) will already be replaced by BERT embeddings.

Q4. We often hear “The original book was way better than the movie!”. 
We are interested to see if the ratings are indeed different. We downloaded various book ratings datasets and we plan to check if the ratings are different in favor of the books in comparison of their movie counterpart.
We first merged the book datasets, rescaled the scores and performed a paired t test. 



## Proposed timeline

| Period                 | Description               |
| ---------------------- | ------------------------- |
|     1st December                   |            Select analysis (Datastory)                |
|          10th December              |               Perform final analysis |
|  15th December  |    Start draft of the datastory     |
| 20th December   | Complete datastory and finetuning until deadline |
| 23rd December | Milestone3 Deadline |


 
## Organization within the team
Q1: Alexander

Q2: Yauheniya

Q3: Aleksandra

Q4: Anahita

Datastory: Together

## Navigating the repo
`Milestone3.ipynb` - main notebook with all pre-processing

All data must be stored on Google Drive in the `ADA` folder

All data that was used can be found at the link: https://drive.google.com/drive/folders/1QFonmS1qnMCpgmxvg2zBNm0M0cqpkNJb?usp=sharing

(The data itself is stored in 3 folders: `WikiData`, `Subtitles`, `MovieSummaries`)


