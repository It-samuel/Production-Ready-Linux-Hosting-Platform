# Production-Ready Linux Hosting Platform

## Overview

This project demonstrates how to build and configure a production-style Linux hosting environment on Microsoft Azure using Ubuntu, Docker, NGINX, and modern DevOps practices.

The platform is designed to simulate how real-world applications are deployed, routed, secured, and managed in cloud environments.

Instead of deploying applications directly onto a server, the system uses Docker containers for workload isolation and NGINX as a reverse proxy for centralized traffic management.

---

# Project Objectives

The goal of this project was to:

* Understand Linux server administration in cloud environments
* Learn production-grade server preparation and hardening
* Deploy multiple applications using Docker containers
* Configure NGINX as a reverse proxy
* Implement HTTPS using Let's Encrypt SSL certificates
* Apply basic production security practices
* Simulate a real-world DevOps hosting workflow

---

# Business Value

This project simulates a lightweight production hosting platform commonly used in startups and enterprise environments.

The system provides:

* Cost-efficient multi-application hosting on a single cloud VM
* Centralized traffic routing using NGINX
* Secure application exposure through HTTPS encryption
* Isolated application environments using Docker
* Improved deployment consistency and maintainability
* Foundational infrastructure for scalable cloud-native systems

---

# Architecture

```text
                Internet
                    |
             HTTPS (SSL)
                    |
              NGINX Reverse Proxy
                    |
      --------------------------------
      |                              |
Frontend Container            Backend API Container
      |                              |
           Ubuntu Linux VM
                    |
               Microsoft Azure
```

---

# Technologies Used

| Technology      | Purpose                       |
| --------------- | ----------------------------- |
| Ubuntu Server   | Linux operating system        |
| Microsoft Azure | Cloud infrastructure          |
| Docker          | Containerization platform     |
| Docker Compose  | Multi-container orchestration |
| NGINX           | Reverse proxy and web server  |
| Flask           | Backend API service           |
| HTML            | Frontend demo application     |
| UFW             | Firewall management           |
| Fail2Ban        | Intrusion prevention          |
| Certbot         | SSL certificate management    |
| Git & GitHub    | Version control               |

---

# Features

## Linux Server Administration

* Azure VM provisioning
* SSH-based remote access
* Linux package management
* System service management
* Production-style directory structure

## Containerization

* Dockerized frontend application
* Dockerized backend API
* Multi-container architecture using Docker Compose
* Container isolation and orchestration

## Reverse Proxy Architecture

* NGINX reverse proxy configuration
* Request routing between services
* Centralized web traffic management

## Security Hardening

* UFW firewall configuration
* Fail2Ban intrusion prevention
* HTTPS with SSL certificates
* Security HTTP headers
* Container restart policies

## DevOps Practices

* Infrastructure organization
* Declarative container management
* Logging awareness
* Version control using GitHub

---

# Project Structure

```text
production-platform/
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── frontend/
│   ├── index.html
│   └── Dockerfile
│
├── nginx/
│   └── production-platform.conf
│
├── docker-compose.yml
└── .gitignore
```

---

# How the System Works

## 1. Incoming Requests

All incoming internet traffic reaches the NGINX reverse proxy.

## 2. Request Routing

NGINX analyzes the request path and routes traffic to the appropriate Docker container.

Example:

* `/` → Frontend container
* `/api` → Backend API container

## 3. Containerized Services

Each application runs independently inside its own Docker container.

This provides:

* workload isolation
* portability
* easier deployments
* environment consistency

## 4. Secure Communication

HTTPS encryption is enabled using Let's Encrypt SSL certificates.

---

# Docker Compose Services

## Frontend Service

Serves the static frontend application using an NGINX container.

## Backend Service

Runs a Flask API application inside a Python container.

---

# Security Configuration

The platform includes multiple production security measures:

| Security Feature | Purpose                             |
| ---------------- | ----------------------------------- |
| UFW Firewall     | Restricts exposed ports             |
| Fail2Ban         | Prevents SSH brute-force attacks    |
| HTTPS SSL        | Encrypts traffic                    |
| Security Headers | Protects against common web attacks |
| Restart Policies | Improves service reliability        |

---

# Ports Used

| Port | Purpose               |
| ---- | --------------------- |
| 22   | SSH                   |
| 80   | HTTP                  |
| 443  | HTTPS                 |
| 3000 | Frontend container    |
| 5000 | Backend API container |

---

# Deployment Steps

## 1. Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/production-linux-platform.git
cd production-linux-platform
```

## 2. Start Containers

```bash
docker compose up -d
```

## 3. Verify Running Containers

```bash
docker ps
```

## 4. Test Applications

Frontend:

```text
http://SERVER_IP
```

Backend:

```text
http://SERVER_IP/api
```

---

# NGINX Reverse Proxy Example

```nginx
server {
    listen 80;

    location / {
        proxy_pass http://localhost:3000;
    }

    location /api {
        proxy_pass http://localhost:5000;
    }
}
```

---

# Challenges Encountered

During development, several real-world infrastructure challenges were encountered:

* Docker container networking
* Reverse proxy routing configuration
* Linux firewall management
* HTTPS setup and SSL validation
* Container port management
* Service orchestration and persistence

These challenges provided practical exposure to real DevOps troubleshooting workflows.

---

# Key Learnings

This project provided hands-on experience with:

* Linux server administration
* Cloud infrastructure management
* Docker containerization
* Reverse proxy architecture
* Infrastructure security hardening
* Multi-service deployments
* Production-style DevOps workflows

---

# Author

Samuel Happiness

Software Engineer | Cloud & DevOps Enthusiast

---

# License

This project is open-source and available for educational and portfolio purposes.
