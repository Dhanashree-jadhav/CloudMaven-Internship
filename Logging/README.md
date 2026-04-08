# 🚀 ELK Stack Setup using Docker Compose

## 📌 Project Overview

### project elk-docker : https://github.com/Dhanashree-jadhav/elk-docker.git

This project demonstrates how to set up a basic **ELK Stack (Elasticsearch + Kibana)** using Docker Compose for local development and testing.

The ELK stack is widely used in DevOps for:

* Log management
* Data analysis
* Real-time monitoring
* Visualization dashboards

---

## 🧱 Architecture

* **Elasticsearch** → Stores and indexes data
* **Kibana** → Visualizes data using dashboards
* **Docker Compose** → Orchestrates both services

---

## ⚙️ Technologies Used

* Docker
* Docker Compose (v3.8)
* Elasticsearch 8.12.0
* Kibana 8.12.0

---

## 📁 Project Structure

```bash
elk-docker/
│── docker-compose.yml
│── README.md
```

---

## 🐳 Docker Compose Configuration

This setup includes two services:

### 🔹 Elasticsearch

* Runs in **single-node mode**
* Security disabled for simplicity
* Port exposed: **9200**

### 🔹 Kibana

* Connects to Elasticsearch
* Provides UI dashboard
* Port exposed: **5601**

Both services are connected via a custom Docker network `elk`.

---

## ▶️ Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone <your-repo-url>
cd elk-docker
```

### 2️⃣ Start the ELK Stack

```bash
docker-compose up -d
```

### 3️⃣ Verify Running Containers

```bash
docker ps
```

---

## 🌐 Access the Services

* 🔍 Elasticsearch:
  http://localhost:9200

* 📊 Kibana:
  http://localhost:5601

---

## 📊 Using Kibana

1. Open Kibana in browser
2. Go to **Integrations → Sample Data**
3. Load sample datasets (e.g., eCommerce)
4. Explore dashboards and visualizations

---

## 🧪 Features Demonstrated

* Containerized ELK setup
* Service communication using Docker network
* Data visualization using Kibana dashboards
* Real-time filtering using KQL (Kibana Query Language)

---

## ❗ Troubleshooting

### 🔴 Kibana not loading

* Wait 30–60 seconds after startup
* Check logs:

```bash
docker logs kibana
```

### 🔴 Elasticsearch issues

```bash
docker logs elasticsearch
```

### 🔴 Port already in use

Change ports in `docker-compose.yml`

---

## 🧠 Key Learnings

* Understanding Docker Compose services
* Connecting containers via networks
* Configuring environment variables
* Visualizing data using Kibana

---

## 🚀 Future Enhancements

* Add **Logstash** for log processing
* Add **Filebeat** to collect logs
* Send application logs (Node.js, Nginx, etc.)
* Create custom dashboards

---

## 💼 Resume Point

> Built and deployed an ELK stack using Docker Compose, enabling real-time data visualization and analysis through Kibana dashboards.

---

## 📌 Notes

* This setup is intended for **local development only**
* Security is disabled for ease of use
* Not recommended for production environments

---
