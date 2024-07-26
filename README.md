# Deploying PostgreSQL on AWS EC2

This repository contains instructions and necessary files to deploy a PostgreSQL database on an AWS EC2 instance using Docker.

## Prerequisites

- An AWS account
- An EC2 instance (already created)
- SSH access to your EC2 instance

## Steps

1. [Connect to your EC2 instance](#1-connect-to-your-ec2-instance)
2. [Install Git](#2-install-git)
3. [Install Docker](#3-install-docker)
4. [Set up PostgreSQL with Docker](#4-set-up-postgresql-with-docker)
5. [Create and configure the database](#5-create-and-configure-the-database)

## Detailed Instructions

### 1. Connect to your EC2 instance

Use SSH to connect to your EC2 instance:

```
ssh -i /path/to/your-key.pem ec2-user@your-ec2-public-dns
```

### 2. Install Git

Update your system and install Git:

```
sudo yum update -y
sudo yum install git -y
```

### 3. Install Docker

Install and start Docker:

```
sudo yum install docker -y
sudo service docker start
sudo usermod -a -G docker ec2-user
```

Log out and log back in for the group changes to take effect.

### 4. Set up PostgreSQL with Docker

Pull the PostgreSQL Docker image and run a container:

```
docker pull postgres
docker run --name my-postgres -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
```


## Additional Files

- `docker-compose.yml`: For easy deployment using Docker Compose
- `init.sql`: Initial SQL commands to set up your database schema
