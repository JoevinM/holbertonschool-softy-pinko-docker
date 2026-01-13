# Docker

## Table of Contents
- [Project Overview](#project-overview)
- [Learning Objectives](#learning-objectives)
- [Requirements](#requirements)
- [Resources](#resources)
- [Table of Tasks](#table-of-tasks)

---

## Project Overview

This project introduces the fundamentals of **Docker containers, Dockerfiles, multi-container networking, Docker Compose, Nginx as a static server, reverse proxy, and load balancing**.

You will build a small containerized infrastructure that includes:
- **A back-end API server** (Flask)
- **A front-end static server** (Nginx)
- **A proxy server** (Nginx reverse proxy)
- **Horizontal scaling** with **Round Robin** load balancing across multiple API servers

This project is part of **Foundations v2.1 — Part 3** and focuses on building practical container-based deployment foundations.

---

## Learning Objectives

By the end of this project, you should be able to explain to anyone, **without Google**:

- what Docker is and why containers are useful
- the difference between **images** and **containers**
- how to write a **Dockerfile** to build a custom image
- how to:
  - build images with `docker build`
  - run containers with `docker run`
  - map ports using `-p HOST:CONTAINER`
- how to containerize a simple **Flask API**
- how to host a static front-end with **Nginx**
- how to connect containers together for front-end ↔ back-end communication
- why **CORS** exists and how to enable it in Flask
- how to orchestrate multiple containers with **docker-compose**
- what a **reverse proxy** does and how to configure it in Nginx
- what **load balancing** is and how **Round Robin** works
- how to scale services horizontally using `docker-compose up --scale`

---

## Requirements

### General

- Docker Desktop must be installed on your **local machine** (not the sandbox)
- Allowed editors: `vi`, `vim`, `emacs`
- All files must:
  - end with a new line
- A `README.md` file is mandatory at the root of the project
- Manual QA review must be requested when the project is complete

### Docker / Project Notes

- Base images used in this project include:
  - `ubuntu:latest` (for back-end tasks)
  - `nginx:latest` (for front-end + proxy tasks)
- When using `apt-get`, always use `-y` to avoid interactive prompts
- If you hit `This environment is externally managed` when installing pip packages, add:
  - `RUN rm /usr/lib/python*/EXTERNALLY-MANAGED`
  before running `pip3 install ...`
- Port mapping uses:
  - `HOSTPORT:CONTAINERPORT`
- For Docker Compose:
  - Use `services`, `build (context/dockerfile)`, `image`, `ports`, and `depends_on`
  - Expose internal ports for container-to-container communication even if they are not mapped to the host

---

## Resources

Read or watch:
- [Docker Desktop](https://www.docker.com/)
- [Docker Tutorial](https://docs.docker.com/get-started/introduction/)
- [Docker cheatsheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
- [Proxy vs Reverse Proxy (Real-world Examples)](https://www.youtube.com/watch?v=4NB0NDtOwIQ)
- [What is a Reverse Proxy? (vs. Forward Proxy) | Proxy servers explained](https://www.youtube.com/watch?v=b_O501x_F68)

---

## Table of Tasks

| # | Task name                               | Description                                                                 | File(s) / Directory |
| - | --------------------------------------- | --------------------------------------------------------------------------- | ------------------- |
| 0 | Create Your First Docker Image          | Build an Ubuntu-based image that updates/upgrades and echoes `Hello, World!`| `task0/Dockerfile` |
| 1 | Back-end                                | Containerize a Flask API with `/api/hello` on port `5252`                   | `task1/Dockerfile`, `task1/api.py` |
| 2 | Front-end                               | Host a static front-end using Nginx on port `9000`                          | `task2/front-end/*`, `task2/front-end/Dockerfile`, `task2/front-end/softy-pinko-front-end.conf` |
| 3 | Connecting the Front-end and Back-end   | Fetch dynamic data from the API and enable CORS in Flask                    | `task3/back-end/*`, `task3/front-end/*` |
| 4 | Making it Simpler with Docker Compose   | Orchestrate front-end + back-end with `docker-compose.yml`                  | `task4/docker-compose.yml` |
| 5 | Proxy Server                            | Add an Nginx reverse proxy routing `/` to front-end and `/api` to back-end  | `task5/proxy/*`, `task5/docker-compose.yml` |
| 6 | Scale Horizontally                      | Run multiple API servers and load-balance requests (Round Robin)            | `task6/2-api-servers.txt` |

---
