
# SPARKIFY ETL Processes

The main goal of this database design is to query:

1. Users data,
2. Songs data, and
3. Users song-playing activities

conveniently for analysis. In this project, we have adpoted a star-schema to design the database.

### Requirements

`Python 3.6.3` is the required python version.

Other required python libraries are detailed in `requirements.txt`


### Instructions

`data` directory contains the data needed for the ETL processes. Add more json files to the corresponding directory to load more data into the database. 

To directly load data into the database, run the following command:

> `python etl.py`


To load data into the database, and have brief summary on the database, open `test.ipynb` and run the cells one by one.


### Database Structure / Schema

##### `songplays` Table

Fact of the star-schema design. It holds all the points that can be referenced by other dimension tables (to be discussed below), such as `song_id`, `user_id`, `artist_id`, ... etc.


##### `users` Table

One of the dimension tables that holds the details of each user. Referenced by `songplays` table using `user_id`.


##### `songs` Table

One of the dimension tables that holds the details of all songs in the database. Referenced by `songplays` table using `song_id`.


##### `artists` Table

One of the dimension tables that holds the details of each artist of all songs. Referenced by `songplays` table using `artist_id`.


##### `time` Table

Last dimension table that holds time data. It is referenced by the `start_time` timestamp in the `songplays` table and used to facilitate time aggregation queries. 


### Sample Query

For example, to find out how many times a song is played, one can run this query:

`SELECT songs.title, COUNT(songplays.song_id) as played_times 
FROM (songplays JOIN songs ON songplays.song_id = songs.song_id) 
GROUP BY songs.title LIMIT 5;`

The following output will be returned


| title          | played_times |
| -------------- | ------------ |
| Setanta matins | 1            |

