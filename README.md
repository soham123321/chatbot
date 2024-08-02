# News Data Pipeline

This project implements a data pipeline that fetches news articles from the NewsAPI, publishes them to a Kafka topic, and stores the articles in a MinIO bucket structured by topic and published date. The entire setup is orchestrated using Docker Compose.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Configuration](#configuration)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Folder Structure in MinIO](#folder-structure-in-minio)
- [License](#license)

## Prerequisites

- Docker
- Docker Compose
- Python 3.6 or higher
- Required Python packages

## Configuration
1. Kafka Configuration: Ensure that the Kafka broker is running and accessible via Docker Compose.
2. MinIO Configuration: Ensure that MinIO is running and accessible via Docker Compose.
3. News API Key: Obtain an API key from NewsAPI and set the news_api_key variable.

## Usage

1. The producer will fetch news articles related to the topic mentioned in the script and publish them to the Kafka topic news. The frequency of the publish can be configured to the user's dicretion
2. The consumer will listen for messages on the topic and upload the articles to MinIO, organized by topic and published date.

## How It Works

Producer:

Fetches news articles from the NewsAPI based on the specified topic.
Publishes the fetched articles to a Kafka topic.

Consumer:

Listens to the Kafka topic for new messages (articles).
Uploads the consumed articles to MinIO, creating a bucket named after the topic and organizing the articles into folders based on the publication date.

## Folder Structure

Bucket Name: The name of the bucket corresponds to the news topic (e.g., "Olympics").
Folder Name: Each folder inside the bucket is named based on the published date of the articles (formatted as YYYYMMDD).
Object Name: Articles are stored as JSON files with names derived from the article title and published time.
