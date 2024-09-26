# Backend Infrastructure Setup

A comprehensive setup for backend infrastructure, featuring three APIs connected to a PostgreSQL database, managed through Docker Compose and a reverse proxy.

## Table of Contents

1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Project Structure](#project-structure)
4. [Getting Started](#getting-started)
   - [Step 1: Clone the Repository](#step-1-clone-the-repository)
   - [Step 2: Build and Run the Services](#step-2-build-and-run-the-services)
   - [Step 3: Access the Services](#step-3-access-the-services)
   - [Step 4: Stopping the Services](#step-4-stopping-the-services)
   - [Step 5: Database Setup](#step-5-database-setup)
5. [Configuration](#configuration)
6. [Troubleshooting](#troubleshooting)

## Overview

This project consists of three microservices: **Order**, **User**, and **Product**. These services are containerized using Docker and managed via Docker Compose. Additionally, PostgreSQL is included as a database, and NGINX is used as a reverse proxy to route requests to the appropriate services.

## Prerequisites

- Docker
- Docker Compose

## Project Structure
```
/backend-infra-setup
│ 
├── docker-compose.yml 
├── nginx 
│   └── nginx.conf 
├── orders 
│   ├── Dockerfile 
|   ├── package.json
|   ├── package-lock.json  
│   └── ... 
├── user  
│   ├── Dockerfile 
|   ├── package.json
|   ├── package-lock.json  
│   └── ... 
└── products
|   ├── Dockerfile 
|   ├── package.json
|   ├── package-lock.json  
|   └── ...
```


## Getting Started

### Step 1: Clone the Repository

```bash
git clone https://github.com/NaveenShanmugavel18/backend-infra-setup.git
cd backend-infra-setup
```

### Step 2: Build and Run the Services
Run the following command to build and start all the services defined in the docker-compose.yml file:

```bash 
docker compose up --build
```


This command will:

- Build the Docker images for each of the services.
- Start the PostgreSQL database.
- Start the Order, User, and Product services.
- Start the NGINX reverse proxy.

### Step 3: Access the Services
Once the services are up and running, you can access them through the NGINX reverse proxy.

- Order Service: http://localhost/orders
- User Service: http://localhost/users
- Product Service: http://localhost/products

Make sure to replace localhost with your Docker host if you're not running it locally.

### Step 4: Stopping the Services
To stop the running services, use:

```bash
docker-compose down
```

### Step 5: Database Setup
The PostgreSQL service is set up automatically by the Docker Compose file. You can adjust the environment variables in the docker-compose.yml file to customize your database connection settings.

### Configuration
You can customize the services and their configurations in their respective `Dockerfile` and application files. The NGINX configuration file (`nginx/default.conf`) can also be modified to suit your routing needs.

### Troubleshooting
- Ensure Docker and Docker Compose are installed correctly.
- Check Docker logs for any issues with service startup:

```bash
docker-compose logs
```

- Verify that the ports specified in the docker-compose.yml file are not being used by other applications.