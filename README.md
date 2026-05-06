Example Voting App

A simple distributed voting application built using multiple Docker containers and deployed with Docker Compose, Docker Swarm, and Kubernetes.

 Project Overview

This project demonstrates a microservices-based application architecture where multiple services communicate with each other using containers. It is designed to showcase containerization, orchestration, networking, and deployment concepts in DevOps.

The application allows users to vote between two options, stores the votes in a database, and displays live voting results.

 Technologies Used
Frontend: Python Flask
Result Application: Node.js
Worker Service: .NET Core
Message Broker: Redis
Database: PostgreSQL
Containerization: Docker
Container Orchestration: Docker Compose, Docker Swarm, Kubernetes
 Application Architecture

The application consists of the following services:

Vote Service (Python Flask)
Provides a web interface for users to vote.
Redis Service
Acts as a message queue and temporarily stores votes.
Worker Service (.NET)
Reads votes from Redis and processes them.
PostgreSQL Database
Permanently stores voting data.
Result Service (Node.js)
Displays voting results in real time.
 Project Structure
example-voting-app/
│
├── vote/                     # Python voting application
├── result/                   # Node.js result application
├── worker/                   # .NET worker service
├── docker-compose.yml        # Docker Compose configuration
├── docker-stack.yml          # Docker Swarm deployment file
├── k8s-specifications/       # Kubernetes YAML files
└── README.md
 Prerequisites

Before running the project, install the following:

Docker Desktop
Docker Compose
Kubernetes
kubectl
 Running the Application using Docker Compose
Step 1: Clone the Repository
git clone <repository-url>
cd example-voting-app
Step 2: Start the Containers
docker compose up
Step 3: Access the Application
Service	URL
Voting App	http://localhost:8080

Result App	http://localhost:8081
 Running the Application using Docker Swarm
Step 1: Initialize Docker Swarm
docker swarm init
Step 2: Deploy the Stack
docker stack deploy --compose-file docker-stack.yml vote
Step 3: Verify Services
docker service ls
 Running the Application in Kubernetes

The Kubernetes deployment files are available inside the k8s-specifications folder.

Step 1: Deploy Resources
kubectl create -f k8s-specifications/
Step 2: Access the Services
Service	Port
Voting App	31000
Result App	31001
Step 3: Delete Kubernetes Resources
kubectl delete -f k8s-specifications/
 Workflow of the Application
User submits a vote through the web interface.
Vote data is sent to Redis.
Worker service retrieves votes from Redis.
Votes are stored in PostgreSQL.
Result service fetches data from PostgreSQL.
Live voting results are displayed to users.
 Features
Multi-container application
Real-time vote processing
Docker Compose deployment
Docker Swarm deployment
Kubernetes deployment
Persistent database storage
Microservices architecture
Container networking
 Learning Outcomes

This project helps in understanding:

Docker containerization
Multi-container communication
Docker Compose
Docker Swarm orchestration
Kubernetes deployments and services
Redis message queues
PostgreSQL integration
Microservices architecture
🛠️ Useful Commands
Stop Containers
docker compose down
View Running Containers
docker ps
View Kubernetes Pods
kubectl get pods
View Kubernetes Services
kubectl get svc
 Conclusion

The Example Voting App demonstrates how modern distributed applications can be deployed using containerization and orchestration technologies. It provides hands-on experience with Docker, Kubernetes, Redis, PostgreSQL, and microservices communication, making it an ideal DevOps learning project.
