# Sparkify AWS-ERM PySpark ETL

The following project is part of UDACITY - Data Engineer Nanodegree. It consist in creating an ETL utalizing AWS-EMR, PySpark and S3.


### Project Description

A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

The project consist in building an ETL pipeline that extracts their data from S3, transform them using Pyspark into a set of dimensional tables, and save them to S3 in parquet format.

### Datasources

##### Song Dataset
The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

##### Song Dataset
The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.

The log files in the dataset you'll be working with are partitioned by year and month.

### File Structure

- **dl.cfg**: Contains credentials for the IAM user that read/writes from/to AWS S3.
- **etl.py**: application code, that performs the extractions, transformation and saves the data back to S3.

*.gitignore, and .gitattributes are helper files to communicate with github.*

### Execution Instructions

1. Fill **dl.cfg** with your AWS User 'Access key ID' and 'Secret access key'. This user must have read and write access to S3.
2. Send **dl.cfg** and **etl.py** to the cluster. They should be in the same folder
3. To execute you must do spark-summit on etl.py and pass the address of the output bucket as parameter. e.g: `spark-submit etl.py s3://output-bucket-name/`


### Output tables
The output is:

```
s3://bucket-name/
|--parquet
|-----artists.parquet/
|-----songplays.parquet/
|-----songs.parquet/
|-----time.parquet/
|-----users.parquet/

