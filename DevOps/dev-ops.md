## Task Description

Your task is to **design, implement, and deploy two services (locally)** that communicate via a **message queue system**.

- The two services can be written in **any programming language** of your choice.
- The services must **communicate asynchronously** using any messaging system, like for example:
    - RabbitMQ
    - NATS
    - MQTT

You are free to pick any tools and frameworks for solving this exercise.

---
## Requirements

- **Service 1**: Publishes a simple message (e.g., a "ping" or a short JSON message) to a topic or queue periodically.
    
- **Service 2**: Subscribes to the topic or queue and processes (e.g., prints/logs) incoming messages.
    
- **Local Deployment**:
    - Use **Docker** to containerize both services.
    - Set up a **local deployment** using either plain Docker commands or `docker-compose`.

- **Message Broker**:
    - Deploy the chosen messaging system also locally (containerized).

---
## Optional Challenge 1

- Add a `health` endpoint to the services which provides some information about their runtime operation, for example a counter of the exchanged messages.
- Monitor this endpoint using **prometheus**
- Add **graphana** to your setup and create a very simple dashboard which displays those metrics.

---
## Optional Challenge 2

- Deploy the services and the message broker using a **local Kubernetes cluster** of your choice.    
- Provide Kubernetes manifests (`.yaml`) or Helm charts for the deployment.

---
## Deliverables

- A **private Git repository** (e.g., GitHub, GitLab) containing:
    - Source code for both services.
    - `Dockerfile`s and optionally `docker-compose.yml` or Kubernetes manifests.
    - Documentation in form of a readme file.
