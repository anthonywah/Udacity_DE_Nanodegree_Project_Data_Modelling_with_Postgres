
# SPARKIFY ETL Processes

The main goal of this database design is to query:

1) Users data,
2) Songs data, and
3) Users song-playing activities

conveniently for analysis. In this project, we have adpoted a star-schema to design the database.


### "songplays" Table

Fact of the star-schema design. It holds all the points that can be referenced by other dimension tables (to be discussed below), such as `song_id`, `user_id`, `artist_id`, ... etc.


### "users" Table

One of the dimension tables that holds the details of each user. Referenced by `songplays` table using `user_id`.


### "songs" Table

One of the dimension tables that holds the details of all songs in the database. Referenced by `songplays` table using `song_id`.


### "artists" Table

One of the dimension tables that holds the details of each artist of all songs. Referenced by `songplays` table using `artist_id`.


### "time" Table

Last dimension table that holds time data. It is referenced by the `start_time` timestamp in the `songplays` table and used to facilitate time aggregation queries. 


