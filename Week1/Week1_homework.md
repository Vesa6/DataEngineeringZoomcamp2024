Docker & SQL
In this homework we'll prepare the environment and practice with Docker and SQL

## Question 1. Knowing docker tags
Run the command to get information on Docker

docker --help

Now run the command to get help on the "docker build" command:

docker build --help

Do the same for "docker run".

Which tag has the following text? - Automatically remove the container when it exits

--delete
--rc
--rmc
--rm

### Answer: The --rm option automatically removes the container when it exits.

## Question 2. Understanding docker first run
Run docker with the python:3.9 image in an interactive mode and the entrypoint of bash. Now check the python modules that are installed ( use pip list ).

What is version of the package wheel ?

### Answer:

![image](https://github.com/user-attachments/assets/f2a72cf5-4455-4de2-8a5d-de5c0bbe5481)

Commands used to build and run:
```
docker build -t test:pandas .
docker run -it test:pandas
```

## Question 3. Count records
How many taxi trips were totally made on September 18th 2019?

Tip: started and finished on 2019-09-18.

Remember that lpep_pickup_datetime and lpep_dropoff_datetime columns are in the format timestamp (date and hour+min+sec) and not in date.

15767

15612

15859

89009

## Question 4. Longest trip for each day
Which was the pick up day with the longest trip distance? Use the pick up time for your calculations.

Tip: For every trip on a single day, we only care about the trip with the longest distance.

2019-09-18

2019-09-16

2019-09-26

2019-09-21

## Question 5. Three biggest pick up Boroughs
Consider lpep_pickup_datetime in '2019-09-18' and ignoring Borough has Unknown

Which were the 3 pick up Boroughs that had a sum of total_amount superior to 50000?

"Brooklyn" "Manhattan" "Queens"

"Bronx" "Brooklyn" "Manhattan"

"Bronx" "Manhattan" "Queens"

"Brooklyn" "Queens" "Staten Island"

## Question 6. Largest tip
For the passengers picked up in September 2019 in the zone name Astoria which was the drop off zone that had the largest tip? We want the name of the zone, not the id.

Note: it's not a typo, it's tip , not trip

Central Park

Jamaica

JFK Airport

Long Island City/Queens Plaza

Terraform

In this section homework we'll prepare the environment by creating resources in GCP with Terraform.

In your VM on GCP/Laptop/GitHub Codespace install Terraform. Copy the files from the course repo here to your VM/Laptop/GitHub Codespace.

Modify the files as necessary to create a GCP Bucket and Big Query Dataset.

## Question 7. Creating Resources
After updating the main.tf and variable.tf files run:

terraform apply

Paste the output of this command into the homework submission form.
