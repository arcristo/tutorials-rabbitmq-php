# RabbitMQ Tutorials

This project provides an environment to follow the
[RabbitMQ Tutorials](https://www.rabbitmq.com/getstarted.html)
using PHP. The environment is set up using Docker and Docker Compose.

## Requisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Project structure

Folder | Description
------------ | -------------
.docker | Contains scripts and config files to build the environment for the project

## Installation

### Prepare the environment

Create the .env file using .env.dist as template and set the variables:

Variable | Description
------------ | -------------
DEV_COMPOSER_HOME | The local folder where to keep the composer files
RABBITMQ_DEFAULT_PASS | The default password for RabbitMQ 
RABBITMQ_DEFAULT_USER | The default user for RabbitMQ
SYSTEM_USER_PHP | The user which runs the commands on the PHP container

Build the images:

```bash
./.docker/bin/docker-build
```

Run the containers:

```bash
./.docker/bin/docker-up
```

To stop the containers run:

```bash
./.docker/bin/docker-down
```

### Install the dependencies

Install the dependencies via composer:

```bash
./.docker/bin/composer install
```
