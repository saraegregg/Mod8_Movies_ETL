
---
## ETL:Extract, Transform, Load
---
### Project Overview
AmazingPrime Video, a platform for streaming movies and TV shows online, wants to host a hack-a-thon with the goal of inspiring their team, having fun, and conncting to the local coding community. In order to do this, they need to provide a clean data set of movies to the participants, who will be asked to write an algorythm that predicts the popular movies. 

### Challenge Objectives

- Create an automated ETL pipeline.
- Extract data from multiple sources.
- Clean and transform the data automatically using Pandas and regular expressions.
- Load new data into PostgresSQL.

### Resources
**Data Sources**
- movies_metadata.csv
- ratings.csv
- wikipedia-movies.json
- ETL_Deliverable1_starter_code.ipynb
- ETL_Deliverable2_starter_code.ipynb
- ETL_Deliverable3_starter_code.ipynb

**Software**
- Jupyter Notebook 6.4.5
- Python 3.9.7
- Anaconda Navigator 1.9.0
- PostgressSQL 12.0

### Summary
In the  course of completing the challenge, I used code written throughout the module and refactored it in four main steps.

First I wrote a function named extract_transform_load() that would read the three data files and convert them to DataFrames.

![challenge_step_1.png](https://github.com/saraegregg/Mod8_Movies_ETL/blob/main/resources/challenge_step_1.png)

The second step is to clean the Wikipedia data. I added the clean movie function from the module and added to the  extract_transform_load() function steps to do the following cleaning tasks:
- remove the entries on tv shows
- drop duplicate imdb entries
- drop columns with large amounts of null values
- convert data to strings and select the useful information from them using regular expressions
- convert datatypes for the box office, budget, release date, and running time columns
The resulting product is a clean DataFrame.

![challenge_step_2.png](https://github.com/saraegregg/Mod8_Movies_ETL/blob/main/resources/challenge_step_2.png)

Afterwards, I focused on cleaning the Kaggle data. I merged the Kaggle and Wiki Movies DataFrames and dropped unnecessary columns from the resulting DataFrame, movies_df. I then dropped unnecessary columns and added the function I wrote in the module to fill any data missing from the Kaggle set in the movies_df DataFrame. I filtered it to keep the columns I needed and renamed them. Then I cleaned the ratings counts, merged it with movies_df, and assigned the value of zero to any null values in a rating category.

Finally, I created the Movie Database in PostgressSQL, making sure that any data that was in the database's movies table is replaced by the new data, and it correctly imports the MovieLens ratings.

![movies_query.png](https://github.com/saraegregg/Mod8_Movies_ETL/blob/main/resources/movies_query.png)
![ratings_query.png](https://github.com/saraegregg/Mod8_Movies_ETL/blob/main/resources/ratings_query.png)
