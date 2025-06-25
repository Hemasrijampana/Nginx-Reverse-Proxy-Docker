# Nginx-Reverse-Proxy-Docker

#  Nginx Reverse Proxy + Docker Compose Deployment on AWS EC2

A DevOps project to deploy two microservices — one in **Golang** and one in **Python Flask** — containerized using Docker Compose, reverse proxied via **Nginx (inside a Docker container)**, and hosted on an **AWS EC2 instance**.

---

##  Table of Contents

1. Project Overview
2. Project Structure
3. Technology Stack
4. Setup and Installation
5. Running the Project
6. API Endpoints
7. Health Checks
8. Vulnerability Scanning
9. Conclusion

---

##  Project Overview

- Two backend services:
  -  Golang Service (`service_1`)
  -  Python Flask Service (`service_2`)
- Nginx reverse proxy container routes:
  - `/service1` → Service 1
  - `/service2` → Service 2
- All services accessible via **port 8080**
- Health checks implemented for both services
- Deployed on **AWS EC2 Ubuntu instance**

---

##  Project Structure

ASSIGNMENT/
├── docker-compose.yml
├── nginx/
│   ├── nginx.conf
│   └── Dockerfile
├── service\_1/
│   ├── main.go
│   └── Dockerfile
├── service\_2/
│   ├── app.py
│   └── Dockerfile
└── README.md



---

##  Tech Stack

- Docker & Docker Compose
- Nginx
- Golang
- Python Flask
- AWS EC2 (Ubuntu 24.04)
- Trivy (for vulnerability scanning)

---

##  Setup & Installation

1️. Launch EC2 Instance
- Launch an **Ubuntu 24.04** instance.
- Add **Inbound rules**:
  - SSH (22)
  - HTTP (80)
  - Custom TCP 8080 (0.0.0.0/0)

---

##  Install Dependencies

SSH into EC2:
```bash
ssh -i <key.pem> ubuntu@<ec2-public-ip>


Install Docker

sudo apt update && sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker


Install Docker Compose:
sudo apt install docker-compose-plugin -y


Install Docker Compose:
sudo apt install docker-compose-plugin -y

Check versions:
docker --version
docker compose version


Clone the Project
git clone https://github.com/Hemasrijampana/Nginx-Reverse-Proxy-Docker.git
cd Nginx-Reverse-Proxy-Docker

Running the Project:
sudo docker compose up --build -d


Check container status:
sudo docker ps


API Endpoints
Method	Path	Response Example
GET	/service1/ping	{"status":"ok","service":"1"}
GET	/service1/hello	{"message":"Hello from Service 1"}
GET	/service2/ping	{"status":"ok","service":"2"}
GET	/service2/hello	{"message":"Hello from Service 2"}

Access from browser or terminal:
http://<ec2-public-ip>:8080/service1/ping
http://<ec2-public-ip>:8080/service2/hello

Health Checks
Check health status:
sudo docker inspect --format='{{json .State.Health}}' service1
sudo docker inspect --format='{{json .State.Health}}' service2


View container logs:
sudo docker logs service1
sudo docker logs service2
sudo docker logs nginx


Conclusion
✔ Successfully containerized two microservices
✔ Configured Nginx reverse proxy with URL-based routing
✔ Orchestrated using Docker Compose
✔ Deployed and secured on AWS EC2
✔ Implemented health checks & basic image scanning



