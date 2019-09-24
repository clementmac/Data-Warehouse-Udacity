PROJECT 3 = song play analysis with S3 and Redshift

INTRODUCTION

- we will use AWS(S3) and Redshift
- data sources are provided by 2 S3 buckets
- both buckets have data in JSON format
- song bucket has everything under same directory
- event bucket has to be extracted from a path with a descriptor file
- Redshift will be used to load and transform data with COPY command
- data will be copied from buckets to staging tables

STAR SCHEMA

-To represent this context a Star schema has been used 

The songplays table is the fact table of this schema and 
it contains foreign keys to four tables;

start_time REFERENCES time(start_time)
user_id REFERENCES time(start_time)
song_id REFERENCES songs(song_id)
artist_id REFERENCES artists(artist_id)

There are also two staging tables; One for song dataset and one for 
and one for event dataset



HOW TO RUN

- create IAM role with AmazonS3ReadOnlyAccess
- create redshift cluster in AWS portal with the default settings
- open the RUN_ME.ipynb and run the 'create_tables.py' and then the 'etl.py' files.

PROJECT FILE DESCRIPTION 

- create_tables.py - This script will drop old tables and re-create new tables
- etl.py - This script executes the queries that extract JSON data from the S3 bucket and load them to Redshift
- sql_queries.py - This file contains variables with SQL statement , separated by CREATE, DROP, COPY and INSERT statements
- dhw.cfg - Configuration file used that contains info about Redshift, IAM and S3
