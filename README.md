# GovHack 2021

Welcome to GovHack 2021. Confluent are proud to be international sponsors of this important event.

This repository is designed to help you get access to a number of live COVID datasets to come up with something great.

# Getting started
1. Clone this repository to your local development machine.
2. Request your Connect configuration file (`worker.properties`) from a Confluent representative.
3. Copy the file to `./config/worker.properties`. *Note: this file will be ignored by git to stop your private connection details ending up in a repo.*
4. Save the file.
5. Launch the connect container using the `docker compose up` command.

This should launch a stand-alone connect worker (that is the software that is reponsible for running connectors). It will then create an instance of a sample connector. This is a simple connector that will connect to Confluent Cloud, read events from a 'topic', and then output the data to `./config/test.sink.txt`.

If you see this file congratulations! You have just consumed from Confluent Cloud.

# Next steps
As nice as it is to have a text file that is being updated each time the COVID data is updated, you might want to ingest this data into another system. 

Confluent provide access to a large range of connectors via [Confluent Hub](https://confuent.io/hub). 

We have installed a small range of common connectors as part of the Docker Compose build. 

## Generic connectors installed 
* [JDBC](https://docs.confluent.io/kafka-connect-jdbc/current) - A generic connector for integrating with relational database
* [HTTP](https://docs.confluent.io/kafka-connect-http/current/overview.html) - A generic connector for integrating with a downstream API

## Specific connectors installed
* [MongoDB](https://github.com/mongodb/mongo-kafka/blob/master/README.md)
* [ElasticSearch](https://docs.confluent.io/kafka-connect-elasticsearch/current/overview.html)
* [Snowflake](https://docs.snowflake.com/en/user-guide/kafka-connector.html)
* [BigQuery](https://docs.confluent.io/kafka-connect-bigquery/current/index.html)
* [Neo4J](https://neo4j.com/labs/kafka/4.0/)

## Adding additional connectors
It is very easy to install additional connectors in your docker environment. Just open up the `docker-compose.yml` and toward the end you will see a block of lines starting with confluent-hub install. This is a simple command line way of installing connectors on a connect worker. So, to add additional connectors:
1. Visit [Confluent Hub](https://confuent.io/hub) and search for the desired connector
2. Copy the `confluent-hub` install command
3. Paste it under the last install command in the `docker-compose.yml` file. Remember to add the `--no-prompt` option to the command - this allows it to be installed without waiting for use input.
4. Restart your docker compose environment.
5. Profit.

# Montioring connectors
The connect worker provides a restful interface for monitoring connectors. Full documentation of that API can be found at https://docs.confluent.io/platform/current/connect/references/restapi.html

Using the API can be really helpful if you need to check the status of a connector, find out what connectors are running, or even restart a connector.

# Additional resources
If you are not that familiar with event streaming (you really want to be!) the absolute, hands down, best place you can go is https://developer.confluent.io. This site has a wealth of content - check out the patterns library to understand how event streaming fits into the bigger architecture picture.

Also, the https://docs.confluent.io site should be very helpful.

# Okay, I want to take this to the next level
Consuming from Confluent Cloud is great, but you might want to use event streaming in yoru application. This, in our opinion, is a great idea. Modern application architectures are placing Event Streaming right at the centre.

Well, good news. You can spin up your own Confluent Cloud organisation and get building. What's more - we will give you $200 USD credit each month for the first three months so that you don't have to pay to get started.

Sign up at https://www.confluent.io/get-started-v1/

Remember, Confluent representatives will be around during the event to help you build your apps.

# Pro tip
You can use some of the $200 toward support. Developer support is only $29/month, so enable it for extra knowledgebase articles and access to Confluents world-class support team. 

Signing up is easy - enable it through the Confluent Cloud UI.
