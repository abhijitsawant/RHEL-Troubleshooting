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
