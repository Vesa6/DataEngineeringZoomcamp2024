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
