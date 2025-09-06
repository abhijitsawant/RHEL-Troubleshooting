# Docker & Docker Compose Guide

This document provides commonly used Docker and Docker Compose commands for managing containers, images, and services.

---

## Table of Contents
- [Docker Basics](#docker-basics)
- [Image Management](#image-management)
- [Container Management](#container-management)
- [Logs & Exec](#logs--exec)
- [Networks & Volumes](#networks--volumes)
- [Docker Hub](#docker-hub)
- [Docker Compose](#docker-compose)
- [Example docker-compose.yml](#example-docker-composeyml)

---

## Docker Basics
```bash
docker --version                 # Check Docker version
docker info                      # System-wide info
docker system df                 # Disk usage by images/containers
docker system prune              # Clean up unused objects

---

## Image Management
```bash
docker images                    # List local images
docker pull ubuntu:20.04         # Pull an image from Docker Hub
docker rmi <image_id>            # Remove an image
docker build -t myapp:1.0 .      # Build image from Dockerfile
docker tag myapp:1.0 myrepo/myapp:1.0   # Tag image for a repo
docker push myrepo/myapp:1.0     # Push to Docker Hub
