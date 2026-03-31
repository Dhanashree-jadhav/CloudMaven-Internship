# 🚀 Docker Compose – MERN Stack Setup

## 📌 Project Overview

* This project is a **containerized MERN stack application** using Docker Compose.
* It consists of three main services:

  * **MongoDB** → Database
  * **Node.js (bezkoder-api)** → Backend API
  * **React + Nginx (bezkoder-ui)** → Frontend UI
* All services run in separate containers and communicate using Docker networks.

---

## 🏗️ Architecture

```
User (Browser)
   ↓
Frontend (React + Nginx)
   ↓
Backend (Node.js API)
   ↓
MongoDB Database
```

---

## ⚙️ Docker Compose Configuration

The `docker-compose.yml` file defines and manages all services in a single place.

### Version

```yaml
version: '3.8'
```

* Specifies Docker Compose version
* Ensures compatibility with modern features

---

## 🧩 Services

### 1. MongoDB Service

```yaml
mongodb:
  image: mongo:5.0.2
  restart: unless-stopped
  env_file: ./.env
  environment:
    - MONGO_INITDB_ROOT_USERNAME=$MONGODB_USER
    - MONGO_INITDB_ROOT_PASSWORD=$MONGODB_PASSWORD
  ports:
    - $MONGODB_LOCAL_PORT:$MONGODB_DOCKER_PORT
  volumes:
    - db:/data/db
  networks:
    - backend
```

**Features:**

* Uses official MongoDB image
* Automatically restarts if stopped
* Loads credentials from `.env`
* Stores data persistently using volumes
* Accessible only within backend network

---

### 2. Backend Service (bezkoder-api)

```yaml
bezkoder-api:
  depends_on:
    - mongodb
  build: ./bezkoder-api
  ports:
    - $NODE_LOCAL_PORT:$NODE_DOCKER_PORT
  environment:
    - DB_HOST=mongodb
    - DB_USER=$MONGODB_USER
    - DB_PASSWORD=$MONGODB_PASSWORD
    - DB_NAME=$MONGODB_DATABASE
    - DB_PORT=$MONGODB_DOCKER_PORT
  networks:
    - backend
    - frontend
```

**Features:**

* Built from local backend source code
* Starts after MongoDB
* Uses service name (`mongodb`) for database connection
* Connects to both frontend and backend networks

---

### 3. Frontend Service (bezkoder-ui)

```yaml
bezkoder-ui:
  depends_on:
    - bezkoder-api
  build:
    context: ./bezkoder-ui
    args:
      - REACT_APP_API_BASE_URL=$CLIENT_API_BASE_URL
  ports:
    - $REACT_LOCAL_PORT:$REACT_DOCKER_PORT
  networks:
    - frontend
```

**Features:**

* Builds React application
* Uses Nginx to serve frontend
* Communicates with backend via API
* Connected only to frontend network

---

## 💾 Volumes

```yaml
volumes:
  db:
```

* Named Docker volume
* Ensures persistent storage for MongoDB
* Prevents data loss

---

## 🌐 Networks

```yaml
networks:
  backend:
  frontend:
```

* **Backend Network:** Used by MongoDB and backend
* **Frontend Network:** Used by frontend and backend
* Provides isolation and secure communication

---

## 🔐 Environment Variables

This project uses a `.env` file to manage:

* MongoDB credentials
* Port configurations
* API base URL

⚠️ Ensure the `.env` file is present before running the project.

---

## ▶️ How to Run the Project

### Step 1: Build and Start Containers

```bash
docker-compose up --build
```

### Step 2: Access Application

* **Frontend:** http://localhost:8888
* **Backend API:** http://localhost:8080/api

---

## 📚 Key Concepts Used

* Multi-container architecture
* Docker Compose orchestration
* Service-to-service communication using container names
* Persistent storage using volumes
* Network isolation (frontend & backend)
* Environment variable management

---

## 🎯 Conclusion

This project demonstrates how to:

* Deploy a full-stack MERN application using Docker
* Manage multiple containers efficiently using Docker Compose
* Enable secure communication using networks
* Persist data using Docker volumes

---

## 👩‍💻 Author

**Dhanashree Jadhav**
DevOps & Cloud Enthusiast 🚀
