# Postgres-ETL or SEP: Sparkify ETL Pipeline
SEP is a project for an imaginary startup called Sparkify. This project creates a database based on a star schema to allow analysts to be able to run fast, simplifie, intuitive queries to answer their questions. Star schema format ensures data integrity, as attribute fields do not appear in more than one table.

# SEP files and tables:
the SEP project includes seven files but three files are required to run the script
* sql_queries.py - Necessary - contains all sql queries.
* create_tables.py - Necessary - drops and creates tables
    * Fact Table
        * songplays - records in log data associated with song plays i.e. records with page NextSong
            * songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
    
    * Dimension Tables
        * users - users in the app
            * user_id, first_name, last_name, gender, level
        * songs - songs in music database
            * song_id, title, artist_id, year, duration
        * artists - artists in music database
            * artist_id, name, location, latitude, longitud
        * time - timestamps of records in songplays broken down into specific units
            * start_time, hour, day, week, month, year, weekday
* etl.ipynb - reads and processes a single file and loads the data into tables. 
* etl.py - Necessary - reads and processes all files and loads them into tables.
    * process_song_file() - open song file, insert song and artist record
    * process_log_file() - open log file, insert time data, user, songplay records
    * process_data() - get all files matching extension from directory, total number of files found and iterate over files and process
    * main() - connect to dataset and process all data
* test.ipynb - displays the first few rows of each table
* README.md
* see_DataSet.ipynb

# Prerequisites
All libraries you need to install:

* psycopg2
* ipython-sql
* pandas
* numpy

# How to create the database using SEP:
First, we need to create the database.
`python create_tables.py`
Second, run:
`python3 etl.py`