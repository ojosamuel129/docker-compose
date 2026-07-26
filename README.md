# 🚀 NGINX Container Deployment with Docker Compose

A hands-on guide for spinning up an NGINX web server using Docker Compose. This project serves as a practical introduction to defining services, managing container lifecycles, and working with multi-container orchestration tools.

---

## 📌 Overview

This repository walks through the fundamentals of **Docker Compose** by defining and deploying a standalone **NGINX web server** via a `compose.yml` file.

While Docker Compose shines when orchestrating complex microservices, starting with a single service is the best way to master the core commands for bringing stacks up, monitoring running processes, checking logs, and tearing environments down cleanly.

---

## 🎯 What You'll Learn

* Building a declarative `compose.yml` configuration
* Launching background (detached) container services
* Mapping network ports between host and container
* Monitoring service status and inspecting runtime logs
* Gracefully shutting down and cleaning up Docker resources

---

## ⚙️ Prerequisites

Ensure you have Docker and Docker Compose installed on your system:

* **Windows / macOS:** [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* **Linux:** Docker Engine + Docker Compose Plugin

Verify your environment by running:

```bash
docker --version
docker compose version

```

---

## 📂 Repository Structure

```text
my-compose-lab/
└── compose.yml

```

---

## 🚀 Quick Start Guide

### 1. Initialize Working Directory

Create a dedicated folder for your project and navigate into it:

```bash
mkdir my-compose-lab && cd my-compose-lab

```

---

### 2. Configure `compose.yml`

Create a file named `compose.yml` in your project root with the following configuration:

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"

```

#### 🔍 Configuration Explained

* **`services`**: Declares the individual workloads that make up your application stack.
* **`web`**: The custom logical name assigned to this specific container service.
* **`image: nginx:latest`**: Instructs Docker to pull and run the official NGINX image from Docker Hub.
* **`ports: ["8080:80"]`**: Routes traffic hitting port `8080` on your machine to port `80` inside the container.

---

### 3. Launch the Web Server

Run the stack in the background (detached mode):

```bash
docker compose up -d

```

**What happens behind the scenes:**

* Docker pulls `nginx:latest` (if not cached locally).
* An isolated default network (`my-compose-lab_default`) is provisioned.
* The container `my-compose-lab-web-1` is created and started.

---

### 4. Verify Active Services

Check if the container is running and confirm port bindings:

```bash
docker compose ps

```

*Expected Output:*

```text
NAME                   IMAGE          STATUS          PORTS
my-compose-lab-web-1   nginx:latest   Up              0.0.0.0:8080->80/tcp

```

---

### 5. Access the Web Page

Open your browser of choice and head to:
👉 **`http://localhost:8080`**

You should see the standard **"Welcome to nginx!"** landing page.

---

### 6. Inspect Service Logs

Stream or inspect output logs to troubleshoot or verify requests:

```bash
docker compose logs

```

*Sample Log Output:*

```text
web-1  | /docker-entrypoint.sh: Configuration complete
web-1  | Starting nginx...

```

---

### 7. Tear Down the Environment

When you are finished testing, gracefully stop and delete all created resources:

```bash
docker compose down

```

This cleanly stops the running NGINX container and deletes both the container instance and its dedicated network.

---

## 💡 Essential Commands Reference

| Action | Command |
| --- | --- |
| **Start stack in background** | `docker compose up -d` |
| **Check running services** | `docker compose ps` |
| **View logs** | `docker compose logs` |
| **Stop and remove stack** | `docker compose down` |

---

## 👤 Author

**Samuel Ojo**

*Cloud & DevOps Professional*

* **GitHub:** [@ojosamuel129](https://github.com/ojosamuel129)

---
