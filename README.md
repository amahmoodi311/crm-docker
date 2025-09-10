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
- `screenshots/Screenshot 2025-09-11 004725.png` – Backend running
- `screenshots/crm-doc1.png` – Backend Dockerfile
- `screenshots/crm-doc3.png` – Spring application edits

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

markdown
Copy code

### Screenshots
- `screenshots/Screenshot 2025-09-11 004926.png` – Frontend running
- `screenshots/crm-doc5.png` – Frontend Dockerfile


## Repository Structure

crm-docker/
│
├── backend/
│ ├── Dockerfile # Backend Dockerfile
│ └── commands.txt # Step-by-step backend commands
│
├── frontend/
│ ├── Dockerfile # Frontend Dockerfile
│ └── commands.txt # Step-by-step frontend commands
│
├── screenshots/
│ ├── crm-doc1.png
│ ├── crm-doc3.png
│ ├── crm-doc5.png
│ ├── Screenshot 2025-09-11 004725.png # Backend running
│ └── Screenshot 2025-09-11 004926.png # Frontend running
│
└── README.md # This file

markdown
Copy code

## Notes
- Make sure Docker is installed and running before starting.
- The backend runs on port `8080`.
- The frontend runs on port `5173`.
- Both containers should be attached to the same Docker network (`crm-network`) for connectivity.
- Follow `commands.txt` files for step-by-step commands.

