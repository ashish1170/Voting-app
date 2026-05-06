# 🗳️ Example Voting App

> A cloud-native, microservices-based voting application demonstrating containerization and orchestration with Docker, Docker Swarm, and Kubernetes.

---

## 📌 Overview

The **Example Voting App** is a distributed, multi-container application that lets users vote between two options in real time. Built to mirror real-world production architecture, it showcases how individual services — frontend, backend, worker, message queue, and database — communicate and scale independently inside containers.

Whether you're learning DevOps fundamentals or exploring container orchestration, this project delivers hands-on experience across the full stack.

---

## 🏗️ Architecture

```
          ┌─────────────┐
          │  Vote App   │  ← Python Flask (User Interface)
          └──────┬──────┘
                 │
          ┌──────▼──────┐
          │    Redis    │  ← Message Broker / Queue
          └──────┬──────┘
                 │
          ┌──────▼──────┐
          │   Worker    │  ← .NET Core (Vote Processor)
          └──────┬──────┘
                 │
          ┌──────▼──────┐
          │ PostgreSQL  │  ← Persistent Database
          └──────┬──────┘
                 │
          ┌──────▼──────┐
          │ Result App  │  ← Node.js (Live Results)
          └─────────────┘
```

### Services at a Glance

| Service | Technology | Role |
|---|---|---|
| **Vote** | Python Flask | Web UI for casting votes |
| **Redis** | Redis | Temporary vote queue (message broker) |
| **Worker** | .NET Core | Reads from Redis, writes to PostgreSQL |
| **Database** | PostgreSQL | Persistent vote storage |
| **Result** | Node.js | Real-time results dashboard |

---

## 📂 Project Structure

```
example-voting-app/
│
├── vote/                     # Python Flask voting UI
├── result/                   # Node.js result dashboard
├── worker/                   # .NET Core worker service
├── docker-compose.yml        # Local development with Docker Compose
├── docker-stack.yml          # Production deployment with Docker Swarm
├── k8s-specifications/       # Kubernetes manifests
└── README.md
```

---

## ⚙️ Prerequisites

Ensure the following tools are installed before running the project:

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Kubernetes](https://kubernetes.io/) *(for K8s deployment)*
- [kubectl](https://kubernetes.io/docs/tasks/tools/) *(for K8s deployment)*

---

## ▶️ Running the App

### 🐳 Option 1 — Docker Compose *(Recommended for local dev)*

```bash
# 1. Clone the repository
git clone <repository-url>
cd example-voting-app

# 2. Start all containers
docker compose up
```

| Service | URL |
|---|---|
| Voting App | http://localhost:8080 |
| Result App | http://localhost:8081 |

```bash
# Stop containers
docker compose down
```

---

### 🐝 Option 2 — Docker Swarm *(Multi-node cluster)*

```bash
# 1. Initialize Swarm mode
docker swarm init

# 2. Deploy the stack
docker stack deploy --compose-file docker-stack.yml vote

# 3. Verify running services
docker service ls
```

---

### ☸️ Option 3 — Kubernetes *(Production-grade orchestration)*

```bash
# 1. Deploy all resources
kubectl create -f k8s-specifications/

# 2. Check pods and services
kubectl get pods
kubectl get svc
```

| Service | NodePort |
|---|---|
| Voting App | 31000 |
| Result App | 31001 |

```bash
# Tear down Kubernetes resources
kubectl delete -f k8s-specifications/
```

---

## 🔄 Application Workflow

```
1. User visits the Voting App → casts a vote
2. Vote is pushed to Redis (message queue)
3. Worker service polls Redis → processes the vote
4. Processed vote is stored in PostgreSQL
5. Result App queries PostgreSQL → displays live results
```

---

## 🛠️ Useful Commands

```bash
# View all running containers
docker ps

# View Kubernetes pods
kubectl get pods

# View Kubernetes services
kubectl get svc

# Stop Docker Compose stack
docker compose down
```

---

## 📖 Learning Outcomes

By working through this project, you will gain practical experience with:

- ✅ Docker containerization and image building
- ✅ Multi-container communication and networking
- ✅ Docker Compose for local orchestration
- ✅ Docker Swarm for multi-node deployments
- ✅ Kubernetes Deployments, Services, and Pods
- ✅ Redis as a lightweight message broker
- ✅ PostgreSQL integration in a containerized environment
- ✅ Microservices architecture principles

---

## 📊 Key Features

- 🗳️ Real-time vote casting and results
- 🐳 Three deployment options: Compose, Swarm, Kubernetes
- 🔗 Loosely coupled microservices
- 💾 Persistent data storage with PostgreSQL
- ⚡ Fast in-memory queuing with Redis
- 🌐 Isolated container networking

---

## 📌 Conclusion

The **Example Voting App** is a practical, end-to-end reference project for anyone learning modern DevOps and cloud-native development. It demonstrates how real distributed systems are architected — with independent, scalable services communicating over a network — and gives you hands-on experience deploying them across Docker and Kubernetes environments.

---

> 💡 *Built for learning. Designed for production patterns.*
