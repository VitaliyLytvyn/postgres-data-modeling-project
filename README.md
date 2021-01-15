# Udacity Data Engineering Nanodegree program
## Project: Data Modeling with Postgres

### Intro
A startup called Sparkify is a music streaming app. They need to analyze the data they've been collecting.
The data - files in json format of logs on user activity and metadata on the songs.

To achieve the goal we create a Postgres database and an ETL pipeline that transfers data from files into this database using Python and SQL.

### Database
To meet the analytic focus of Sparkify we build the database with star schema.
#### Fact table 
- 'songplays' - records from log data associated with song plays
    - fields: songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

#### Dimension Tables
- 'users' - users in the app
    - fields: user_id, first_name, last_name, gender, level
- 'songs' - songs info
    - fields: song_id, title, artist_id, year, duration
- 'artists' - artists info
    - artist_id, name, location, latitude, longitude
- 'time' - timestamps of records in 'songplays' broken down into specific units
    - fields: start_time, hour, day, week, month, year, weekday

### ETL pipeline
To prepare database run file 'create_tables.py'. 
It will drop existing database and create the new one with appropriate tables.
SQL queries used in 'create_tables.py' defined in 'sql_queries.py' file.

To start etl pipeline run 'etl.py' file.
It will connect to database and start 2 processing works:
- Reads and processing log files, extracts data relative to user, time and songplay, saves obtained data to database's appropriate tables.
- Reads and processing song files, extracts data relative to songs and artists, saves obtained data to database's appropriate tables.

### Visualization
To visualize the process there are 2 Jupyter Notebook files:
- 'test.ipynb' - displays the first few rows of each table.
- 'etl.ipynb' - reads and processes a single file both from logs and songs metadata directories, then loads the data into the tables.

### UML diagram
![UML diagram](/images/uml.png)