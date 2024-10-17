# 3-Tier-MERN-docker-compose
 A simple MERN (MongoDB, Express, React, Node.js) stack application that demonstrates the use of Docker for containerization.

## Features
- Fully functional MERN stack application
- Dockerized components for easy setup and deployment
- Isolated network for container communication

## Setup

### Create a network for the docker containers
Create a dedicated Docker network for your containers:

`docker network create mern`

### Build the client 

```sh
cd mern/frontend
docker build -t mern-frontend .
```

### Run the client

`docker run --name=frontend --network=mern -d -p 5173:5173 mern-frontend`

### Verify the client is running

Open your browser and type `http://localhost:5173`

### Pull mongodb image 
`docker pull mongo:latest`

### Run the mongodb container

`docker run --network=mern --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest`

### Build the server

```sh
cd mern/backend
docker build -t mern-backend .
```

### Run the server

`docker run --name=backend --network=demo -d -p 5050:5050 mern-backend`

## Using Docker Compose

`docker compose up -d`


