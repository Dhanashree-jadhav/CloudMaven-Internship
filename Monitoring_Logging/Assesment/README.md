# 🚀 Monitoring Implementation using Prometheus & Grafana

### Assesment project link : https://github.com/Dhanashree-jadhav/monitoring-project.git

## 📌 Project Title

Design and Implement a Complete Monitoring Solution for a Containerized Application

---

## 🎯 Objective

This project demonstrates how to:

* Deploy a containerized application
* Set up monitoring using Prometheus and Grafana
* Collect infrastructure and application metrics
* Visualize real-time data using dashboards

---

## 🧱 Tech Stack

* Docker & Docker Compose
* Prometheus (Metrics Collection)
* Grafana (Visualization)
* Node Exporter (System Metrics)
* Node.js (Sample Application)

---

## 📁 Project Structure

```
monitoring-project/
│── app/
│   ├── app.js
│   └── Dockerfile
│
│── prometheus/
│   └── prometheus.yml
│
│── grafana/
│
│── docker-compose.yml
│── README.md
```

---

## ⚙️ Setup Instructions

### 1️⃣ Repository

```
https://github.com/Dhanashree-jadhav/monitoring-project.git
cd monitoring-project
```

---

### 2️⃣ Run the Project

```
docker-compose up --build
```

---

## 🌐 Services & URLs

| Service       | URL                   |
| ------------- | --------------------- |
| Application   | http://localhost:3000 |
| Prometheus    | http://localhost:9090 |
| Grafana       | http://localhost:3001 |
| Node Exporter | http://localhost:9100 |

---

## 🔍 Metrics Collection

### Application Metrics

* `http_requests_total` → Total number of requests

### Infrastructure Metrics

* CPU usage
* Memory usage
* Disk usage

---

## 📊 Grafana Dashboards

### 📊 Dashboard 1: Infrastructure Monitoring

* CPU Usage
* Memory Usage
* Disk Usage

---

### 📈 Dashboard 2: Application Monitoring

* Total Requests
* Requests Per Second → `rate(http_requests_total[1m])`
* Traffic Trend → `increase(http_requests_total[1m])`

---

## 🚀 Traffic Simulation

### For Windows (PowerShell)

```
while ($true) { Invoke-WebRequest http://localhost:3000 -UseBasicParsing | Out-Null; Start-Sleep -Seconds 1 }
```

---

## 🧠 Observability Analysis

### 1. Infrastructure vs Application Metrics

* Infrastructure metrics track system resources like CPU, memory, and disk usage.
* Application metrics track application behavior such as requests and errors.
* Both are essential for complete system monitoring.

---

### 2. Why use `rate()` function?

* Counters only increase over time.
* Raw values are not useful for real-time analysis.
* `rate()` calculates the per-second change.
* Helps in understanding request traffic.

---

### 3. Role of Monitoring in Troubleshooting

* Detects issues early
* Helps identify bottlenecks
* Provides real-time insights
* Reduces downtime

---

## ✅ Conclusion

This project successfully demonstrates a complete monitoring setup using Prometheus and Grafana, providing real-time insights into both infrastructure and application performance.

---

## 👩‍💻 Author

**Dhanashree Jadhav**
