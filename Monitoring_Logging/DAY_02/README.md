# 🚀 Prometheus + Grafana Monitoring with Docker Compose

## 📌 Project Overview

This project demonstrates how to set up a **complete monitoring system** using **Prometheus** and **Grafana** to track and visualize metrics from a simple Node.js application.

The application exposes custom metrics, which are scraped by Prometheus and visualized in Grafana dashboards.

---

## 🏗️ Architecture

```
Node.js App  →  Prometheus  →  Grafana
   (metrics)     (scrape)     (visualize)
```

---

## ⚙️ Tech Stack

* Node.js (Application)
* Prometheus (Monitoring)
* Grafana (Visualization)
* Docker & Docker Compose (Containerization)

---

## 📂 Project Structure

```
prometheus-grafana-demo/
│── docker-compose.yml
│── prometheus.yml
│── app/
│   ├── app.js
│   ├── package.json
│   └── Dockerfile
│── README.md
```

---

## 🚀 Getting Started

### 🔹 Prerequisites

* Docker installed
* Docker Compose installed

---

### 🔹 Run the Project

```bash
docker-compose up --build
```

---

## 🌐 Services & URLs

| Service    | URL                           |
| ---------- | ----------------------------- |
| Node App   | http://localhost:3000         |
| Metrics    | http://localhost:3000/metrics |
| Prometheus | http://localhost:9090         |
| Grafana    | http://localhost:3001         |

---

## 🔐 Grafana Login

```
Username: admin
Password: admin
```

---

## 📊 Metrics Used

### 1. Total Requests

```
node_requests_total
```

### 2. Request Rate (per second)

```
rate(node_requests_total[1m])
```

### 3. Requests in last 5 minutes

```
increase(node_requests_total[5m])
```

---

## 📈 Grafana Dashboard

A custom dashboard was created to visualize:

* Total number of requests
* Request rate (real-time traffic)
* Request trends over time

---

## 🧠 Key Concepts Learned

* Prometheus metrics collection and scraping
* Creating custom metrics using `prom-client`
* Writing PromQL queries (`rate`, `increase`)
* Grafana dashboard creation and visualization
* Containerizing multi-service apps using Docker Compose

---


## 🎯 Outcome

Successfully built a **containerized monitoring pipeline** that:

* Collects application metrics
* Stores them using Prometheus
* Visualizes them in Grafana dashboards

---

## 🚀 Future Improvements

* Add Node Exporter for system metrics (CPU, Memory)
* Implement alerting (Slack / Email)
* Deploy on cloud (AWS / GCP)
* Add more application metrics (response time, errors)

---

