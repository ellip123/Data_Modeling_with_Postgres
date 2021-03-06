# Udacity Data Engineering Nanodegree Program
# Data Modeling with Postgres

## Purpose of Project

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

## Project Description
In this Project, fact and dimension tables will be designed for a star schema for this particular purpose. An ETL pipeline will also be designed to transfer data from files in two local directories into these tables in Postgres using Python and SQL.

## Source Data
Song dataset:

The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

Log dataset:

The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.

## Database schema

This database uses the star schema: One Fact Table and Four Dimension Tables.

#### Fact Table
**songplays** 
- songplay_id INT PRIMARY KEY,
- start_time TIMESTAMP, 
- user_id VARCHAR, 
- level VARCHAR, 
- song_id VARCHAR, 
- artist_id VARCHAR, 
- session_id VARCHAR, 
- location VARCHAR, 
- user_agent VARCHAR

#### Dimension Tables
**users** 
- user_id VARCHAR PRIMARY KEY, 
- first_name VARCHAR, 
- last_name VARCHAR, 
- gender VARCHAR, 
- level VARCHAR

**songs** 
- song_id VARCHAR PRIMARY KEY, 
- title VARCHAR, 
- artist_id VARCHAR, 
- year INT, 
- duration INT

**artists** 
- artist_id VARCHAR PRIMARY KEY, 
- name VARCHAR, 
- location VARCHAR, 
- latitude FLOAT, 
- longitude FLOAT

**time** 
- start_time TIMESTAMP NOT NULL PRIMARY KEY, 
- hour INT, 
- day INT, 
- week INT, 
- month INT, 
- year INT, 
- weekday INT



## File Structure

- `sql_queries.py` - It contains all the sql scripts for drop and create tables for storing song and log information.
- `create_tables.py` - drops and creates tables in postgres database.
- `etl.ipynb` - reads and processes the single file from song_data and log_data and loads the data into the postgres database.
- `etl.py` - reads and processes all the files from song_data and log_data and loads the data into the postgres database.
- `test.ipynb` - displays the rows of each table to validate the data.

## ETL pipeline

  ETL.py will work as following for processing the data:
- Connect to the sparkify datase. And it will drop and create all the tables.
- Parse out each json file and load all of the files into dataframe.
- Song_data and Log_data will be loaded into the fact and dimension tables.

Files will be excuted in the following orders:

- 1.create_tables.py
- 2.etl.py
- 3.test.ipynb

## Summary

This project will provide Sparkify to answer some business question like 'Which are the top popular songs users are listening to".
