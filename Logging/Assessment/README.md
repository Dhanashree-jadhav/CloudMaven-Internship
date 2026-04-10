# 📊 Centralized Logging Setup using ELK

## 📌 Background
In modern applications, logs are often scattered across multiple services, making debugging difficult.  
This project demonstrates a centralized logging system using the ELK stack to improve monitoring and observability.

---

## 🎯 Objective
Build an ELK pipeline that:

- Collects application logs  
- Processes logs (optional)  
- Stores logs centrally  
- Visualizes logs using dashboards  
- Supports filtering and analysis  

---

## 🏗️ Architecture
```
Application → Filebeat → Logstash → Elasticsearch → Kibana
```

- **Application** → Generates logs  
- **Filebeat** → Collects logs  
- **Logstash** → Processes logs  
- **Elasticsearch** → Stores logs  
- **Kibana** → Visualizes logs  

---

## ⚙️ Tech Stack
- Elasticsearch  
- Logstash  
- Kibana  
- Filebeat  
- Docker & Docker Compose  

---

## 🚀 Setup Instructions

### 1️⃣ Clone Repository
```bash
git clone https://github.com/Dhanashree-jadhav/elk-logging-project.git
cd elk-logging-project
```

### 2️⃣ Start ELK Stack
```bash
docker-compose up -d
```

### 3️⃣ Verify Containers
```bash
docker ps
```

---

## 🌐 Access Kibana
Open in browser:

```
http://localhost:5601
```

---

## 📥 Log Ingestion Flow
- Filebeat reads logs from the application  
- Sends logs to Logstash  
- Logstash processes logs and forwards them  
- Elasticsearch stores the logs  

---

## 🔍 Kibana Usage

### 1️⃣ Create Index Pattern
- Go to **Stack Management → Index Patterns**  
- Create pattern: `filebeat-*`

### 2️⃣ View Logs
- Go to **Discover**  
- Select the index pattern  
- View incoming logs  

### 3️⃣ Apply Filters
Example:
```bash
level: "ERROR"
```

---

## 📊 Dashboard
The dashboard includes:

- 📈 Logs Over Time (Line Chart)  
- 📊 Error Count (Bar Chart)  
- 🥧 Log Distribution (Pie Chart)  

---

## 📁 Project Structure
```
├── docker-compose.yml
├── filebeat.yml
├── logstash.conf
├── app/
│   └── sample app generating logs
└── README.md
```

---

