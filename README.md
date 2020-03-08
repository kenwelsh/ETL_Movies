# ETL_Movies

## Challenge

The challenge.ipynb file contains a script that will perform an ETL process on three movie data files (Kaggle files not included in the depository due to size and issues with Git Large File Storage):
+ wikipedia.movies.json
+ movies_metadata.csv (sourced from Kaggle)
+ ratings.csv (sourced from Kaggle)  


Assumptions:
+ The file directory path is currently set to work on my local machine.  You will have to update the path based on your file structure to work on your machine.
+ This assumes that future versions of the three files will be similar in structure and content.
+ Alternate titles are sourced from known alternate title key relationships.  It is possible for additional alternate title key relationships to appear in future version of the wikipedia.movies.json file.
+ The wikipedia.movies.json file has many labels/column names that are similar.  All currently known similar columns are merged in the script, but future Wiki files may contain new column names that will need to be added to the process.
+ Columns in the Wiki data are that have greater than 90% null values are being dropped from the final dataset.  New columns that are not accounted for in later steps of the ETL process could appear with future wiki files if the data becomes more frequently tracked.
+ When merging the wiki data with the Kaggle data, several competing columns were identified.  The following decisions were made:
  + Title: drop Wikipedia column
  + Running Time: keep Kaggle; fill in zeros with Wikipedia data
  + Budget: keep Kaggle; fill in zeros with Wikipedia data
  + Box Office: keep Kaggle; fill in zeros with Wikipedia data
  + Release Date: drop Wikipedia column
  + Original Language: drop Wikipedia column
  + Production Companies: drop Wikipedia column
  + Periodic review of the data to ensure these remain the appropriate choices is recommended.
+ The database load is set up to work with my Postgres account.  Other users will need to create their own config.py file with their credentials to be able to run the script on their local machine.
+ The script is set to delete the existing data from the "movies" table in the "movie_data" database and append the new cleaned data.  The database and table must exist for the script to work.  If future files create additional columns in the cleaned dataset, the movies table will need to be updated to accept the new data.


  
  
  
  
  
