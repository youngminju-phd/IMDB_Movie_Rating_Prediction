# IMDb movie's average rating prediction

## Use the publicly available IMDb Datasets to build a model that predicts a movie’s average rating.


**IMDb Data Source and details:** [IMDb public data](https://www.imdb.com/interfaces/)

**Dataset details:**

The datasets have two important keys: *tconst* and *nconst*.

*tconst:* alphanumeric unique identifier of the title

*nconst:* alphanumeric unique identifier of the name/person

1. **title.akas:** Contains titles' information about the various versions/languages/regions/types. 
2. **title.basics:** Contains titles' basic information like name, type, runtime, startYear, etc.
3. **title.crew:** Contains the director and writer information for all the titles in IMDb.
4. **title.episode:** Contains the tv episode information. (**We don't need this dataset because we will analyze movie**)
5. **title.principals:** Contains the principal cast/crew for titles.
6. **title.ratings:** Contains the IMDb rating and votes information for titles.
7. **names.basics:** Contains basic information about a person like name, birthYear, deathYear, and the titles the person is most known for.


**Repository folders:**
- **data** : Contains dataset files
    - **raw**: files obtained from the web
    - **interim**: data saved after some initial processing like missing value imputation, some primitive feature calculations, etc.
    - **final**: dataset in its final form with all features used to train models.
- **notebooks** : The process is divided into 5 steps each having their separate notebooks (listed in order)
    1. [Data preprocessing](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/1.%20data%20preprocessing.ipynb)
    2. [Feature Engineering](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/2.%20Feature%20Engineering.ipynb)
    3. [Exploratory Data Analysis](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/3.%20Exploratory%20Data%20Analysis.ipynb)
    4. [Data Sampling](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/4.%20Data%20Sampling.ipynb)
    5. [Modeling](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/5.%20Modeling.ipynb)
- **models** : Save trained models

## Process (5 steps):

##### Set the problem as a regression problem, the target(outcome variable) being a movie's average rating.


### 1. Data Preprocessing [Notebook](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/1.%20data%20preprocessing.ipynb):
We process the data at this stage by imputing missing values, dropping rows to keep just those that are needed to reduce computation, and so on. The interim data folder is where we save the intermediate files.

### 2. Feature Engineering [Notebook](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/2.%20Feature%20Engineering.ipynb)
**Popularity Index** is created. We define the popularity index at two types:
- popularity index of people
- popularity index of a title inferred from the popularity index of its cast and crew (actors/directors/writers)

### 3. Exploratory Data Analysis [Notebook](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/3.%20Exploratory%20Data%20Analysis.ipynb)
In this stage, we visualize the dataset and some features to get insights.


### 4. Data Sampling [Notebook](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/4.%20Data%20Sampling.ipynb)
In classification problems, stratified sampling is used to split the train and test data.

Since we have a regression problem, we find the natural clustering of the data using KMeans algorithm and sample equally from each cluster to each of our train and test set.

### 5. Model Building [Notebook](https://github.com/youngminju-phd/IMDB_Movie_Rating_Prediction/blob/main/notebooks/5.%20Modeling.ipynb)
We train models on the final data set to predict a movie's average rating


## Conclusions:
- Best XGBoost model achieved **66%** accuracy on the test set and **70%** accuracy (_r2-score_) on the train set. 

### Reference
https://github.com/kedarbartake98
