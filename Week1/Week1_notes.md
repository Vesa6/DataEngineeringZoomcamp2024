# Notes

## 1.2.1
The point of the docker exercise is to illustrate how Docker can be used to containerize different entities, in this case, an environment consisting of an OS (Ubuntu 20.04) and a data pipeline built with Python 3.9, Pandas and a Postgres connection library.
The final container will contain everything this particular thing needs. 

### Useful applications:

Docker images are useful for transferring the whole container to another machine, so you can run it easily in a different environment, for example, in Google Cloud or AWS.

Another useful application for Docker is to have multiple databases running on one host machine, since this allows complete isolation.

Integration tests (CI/CD)

Running pipelines on the cloud

Spark (Containerize deps like Spark, Hadoop, Java... All the fragile stuff)

Serverless processing (AWS Lambda, Google Functions)

For example, even if you rm rf everything in a Docker container, rebooting it will spin it right back to the beginning.

Dockerfile is basically used for determining what you want the container to do once it starts.
Ex.
```
# Uses python image from Docker Hub as base image
FROM python:3.9

# Install library inside the container w pip
RUN pip install pandas

# Switch to this dir
WORKDIR /app

# Copy local pipeline file into the /app dir inside the container
COPY pipeline.py pipeline.py

#Define default command to use when container starts
ENTRYPOINT [ "python", "pipeline.py" ]
```

## 1.2.2

Some useful commands:

```
-- Grabs the first 100 rows and puts it in a separate file, basic Linux pipe. Didn't know this works on windows Linux-like CLI too!

head -n 100 yellow_tripdata_2021-01.csv > yellow_head.csv
```

```
print(pd.io.sql.get_schema(df, name='yellow_taxi_data'))

Pandas for data definition language conversion, allows u to check datatypes easily.
```

```
Datetime conversion

df.tpep_pickup_datetime = pd.to_datetime(df.tpep_pickup_datetime)
df.tpep_dropoff_datetime = pd.to_datetime(df.tpep_dropoff_datetime)
```


```
while True:

    t_start = time()
    
    df = next(df_iter)

    df.tpep_pickup_datetime = pd.to_datetime(df.tpep_pickup_datetime)
    df.tpep_dropoff_datetime = pd.to_datetime(df.tpep_dropoff_datetime)

    df.to_sql(name='yellow_taxi_data', con=engine, if_exists='append')

    t_end = time()

    print('inserted chunk, took %.3f seconds' % (t_end - t_start))


-- Load a big chunk of data using iter, benchmarking the time it takes for each chunk (also changes timestamps to better format)
-- This just exits on exception - Not the cleanest style but w/e.
```

Tip: Just getting the head can be used to create table (just puts headers in it):
```
df.head(n=0).to_sql(name='yellow_taxi_data', con=engine, if_exists='replace') 
```

