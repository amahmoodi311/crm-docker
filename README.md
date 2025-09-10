# CRM Docker Setup

This repository contains the Docker setup for a CRM application with separate backend and frontend services. It includes:

- Backend Dockerfile and step-by-step commands
- Frontend Dockerfile and step-by-step commands
- Screenshots of Dockerfiles and running applications

## Backend Setup

The backend is a Spring Boot application with PostgreSQL.

### Dockerfile
See `backend/Dockerfile`.

### Commands
Step-by-step commands to build and run the backend:

Navigate to backend

cd crm-api

Build Docker image

docker build -t crm-api .

Create a Docker network (if not already)

docker network create crm-network

Run PostgreSQL container

docker run -d --name crm-db --network crm-network
-e POSTGRES_USER=crmuser
-e POSTGRES_PASSWORD=Admin123
-e POSTGRES_DB=crmdb
-p 5432:5432
postgres:15

Run backend container

docker run -d --name crm-api --network crm-network -p 8080:8080 crm-api

Verify containers

docker ps


### Screenshots
![Backend Dockerfile](https://github.com/amahmoodi311/crm-docker/blob/main/screenshots/crm-doc1.png)
![Backend Running](https://github.com/amahmoodi311/crm-docker/blob/main/screenshots/crm-doc3.png)
![spring.application](https://github.com/amahmoodi311/crm-docker/blob/9f6485dfe97f55399a9fb863bb092685acf6e4f2/Screenshot%202025-09-10%20234737.png)

## Frontend Setup

The frontend is a Vite + React application.

### Dockerfile
See `frontend/Dockerfile`.

### Commands
Step-by-step commands to build and run the frontend:

Navigate to frontend
cd crm-web

Install dependencies
npm install

Build Docker image
docker build -t crm-web .

Run frontend container
docker run -d --name crm-web --network crm-network -p 5173:5173 crm-web

Verify container is running
docker ps



### Screenshots
![Frontend Dockerfile](https://github.com/amahmoodi311/crm-docker/blob/main/screenshots/Screenshot%202025-09-11%20004725.png)
![Frontend Running](https://github.com/amahmoodi311/crm-docker/blob/main/screenshots/Screenshot%202025-09-11%20004926.png)




## Notes
- Make sure Docker is installed and running before starting.
- The backend runs on port `8080`.
- The frontend runs on port `5173`.
- Both containers should be attached to the same Docker network (`crm-network`) for connectivity.
- Follow `commands.txt` files for step-by-step commands.

