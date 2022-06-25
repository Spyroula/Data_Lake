# Data Lake project 
A music streaming startup, Sparkify, has grown their user base and song database even more and want to move their data warehouse to a data lake. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

As an data engineer of Sparkify, I am tasked with building an ETL pipelinefor a data lake hosted on S3. My main goal is to load data from S3 bucket, process the data into analytics tables using Spark, and load the data back into S3 as a set of dimensional tables. We will deploy this Spark process on a cluster using AWS.

The completion of the project will allow the analytics team of Sparkify to continue finding insights in what songs the users are listening to.

## ETL Pipeline
    
1.   The script reads song and log data from an S3 bucket:
    
    -   Song data:  
                
                `s3://udacity-dend/song_data`
                
    -   Log data:  
                
                `s3://udacity-dend/log_data`
        
2.  Spark process on the data
    
    Transforms the loaded data into five different tables, namely:
    
    #### Fact Table
    
    **songplays**  : Log data associated with songs for instance records with page  `NextSong`
           `_songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent_`
    
    #### Dimension Tables
    
    **users**  : users of the app
            `_user_id, first_name, last_name, gender, level_`

    **songs**  : songs in the database
            `_song_id, title, artist_id, year, duration_`
    
    **artists**  : artists in the database
             `_artist_id, name, location, lattitude, longitude_`
    
    **time**  : timestamps of records in the  **songplays**  fact table seperated into specific units
             `_start_time, hour, day, week, month, year, weekday_`
    
3.  The script writes the tables in parquet files and loads them into the S3:
            `"s3a://sparkify-data-lake-udend/"`
    

