# Library Management System – Dockerized Project
## Project Overview

This project demonstrates containerizing a Flask-based Library Management System using Docker. It covers core DevOps concepts like containerization, multi-container architecture, networking, and deployment using Docker Compose.

## Docker Implementation

The application is containerized using Docker by creating custom images and running containers. Key concepts like image creation, container lifecycle management, and volume usage for persistent storage are implemented.

## Networking & Database Integration

Docker networking is used to enable communication between services. The Flask application is connected with a MySQL database running in a separate container, ensuring proper service interaction in an isolated environment.

## Multi-Container Setup (Docker Compose)

Docker Compose is used to manage multiple services including the Flask app, MySQL database, and Nginx server. It simplifies deployment by running all services together with a single command.