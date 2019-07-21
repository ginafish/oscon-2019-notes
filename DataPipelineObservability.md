# Jiaqi Liu - Button - Observability for Data Pipelines

ETL Pipeline
*   Extract
*   Transform (or running through model/aggregating)
*   Load (into warehouse or display to user)

Data Pipeline Example
*   Data scraped from oscon speaker schedule, parsed
*   parsed as csv, uploaded
*   lots of assumptions made - brittle; basically any changes to the website will break it

Wide range of partners with wide range of datasets

Deals with batch and streaming data

Tools for data pipelines:
Luigi, Airflow, AWS data pipeline, Google dataflow


## What could go wrong?

* Batch jobs not scheduled or takes too long
* Data malformed or corrupted - input can be changed with no warning
* Lost data - serice down, lots of places it can be dropped at
* Stream is backed up and data is lost (not properly dead-lettering)
* Non-deterministic models

Stream jobs - look at ingress, egress, oldest age of unprocessed data

It's not enough to know that the pipeline is healthy - you have to have visibility into the dataset itself

Need to support interpretability and observability


## Interpretabliity

Not just the what but the why

Lets you debug and audit machine learning models

Check for causality - that correlations aren't being picked up, but causalities are


## Observability

Testing + monitoring

Need it to be easy to debug

Evidence, not conjecture

Want a mystery free prod


# Pipeline Features

aka how to build observability and interpretability

Immutable data
* Leads to reproducible outcomes
* School of thought that should follow functional programming philosophy

data lineage
* way to understand which version of data, version of code, and which input source created the data
* for diagnostics
* able to do a backfill?
* Tag records with metadata (version of code, source of data)
* Log to a distributed tracer (another service, w/ consistent UIDs)
* want to understand where a data might have changed unexpectedly

test run
* Allow you to validate assumptions
* run a test, check inputs and outputs
* batch processing might have a very long feedback loop
* What assumptions did you make about your data?
    * Document numerical and data type assumptions
* Protocol buffers to define schema
* No ability to test, no way to know what correct behavior is
* If you need to correct an assumption, should to be able to run a backfill
* Integration tests, good

Champion/challenger model used in data science

Health check - check a job has succeeded
Integration test - run continuous test suite that hits GET endpoint to check for expected output
Latency - measure time for pipeline to complete


# Monitoring

They use Prometheus (great for time series data) and Grafana

Used Nagios and StatsSteve, Jenkins previously

Metric types
* Counter - good for tracking # of events or errors (don't use for things that can go down)
* Gauge - good for tracking numerical value that can go up or down (like temporature)
* histogram - configurable bucket, counts number of observations (like a counter)
* summary - sample observations over sliding windows

Page on symptoms, not causes (ex: alert for pipeline failure, server out of memory)

