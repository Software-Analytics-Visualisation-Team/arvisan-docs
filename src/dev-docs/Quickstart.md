---
layout: default
title: Quickstart
nav_order: 1
parent: Developer Documentation
---

# Quickstart Guide for Local Development

This guide walks you through setting up **ARViSAN** for local development. The easiest way to run ARViSAN is via **Docker**, but manual setup with **Neo4j** is also supported.

---

## ✅ 1. Pre-requisites

You need one of the following setups:

### Docker (Recommended)

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

### Alternatively, Local Neo4j Setup

- Install [Neo4j Desktop](https://neo4j.com/download/)

---

## 📦 2. Clone the ARViSAN Repositories

First, create a working directory and clone the repositories:

```bash
mkdir Arvisan
cd Arvisan

git clone https://github.com/Software-Analytics-Visualisation-Team/arvisan-backend.git
git clone https://github.com/Software-Analytics-Visualisation-Team/arvisan-frontend.git
git clone https://github.com/Software-Analytics-Visualisation-Team/arvisan-dependency-parser.git
```

---

## ⚙️ 3. Set Up Docker or Neo4j

### Docker Setup (Recommended)

1. Copy the `docker-compose.yml` and `docker-compose.dev.yml` files from `arvisan-backend` to the **parent** `Arvisan/` folder:

```bash
cp arvisan-backend/docker-compose*.yml .
```

This places the Docker setup at the root where all services can be orchestrated.

---

### Neo4j Manual Setup

1. Start Neo4j Desktop.
2. Create a **new local database** (e.g., named `arvisan-db`).
3. In **Plugins**, install and enable the **APOC** plugin.
4. Start the database and take note of:
   - Bolt URL (e.g., `bolt://localhost:7687`)
   - Username (default: `neo4j`)
   - Password (set during database creation)

---

## 🏃 4. Running ARViSAN

### 4A. Run with Docker

In the **Arvisan** folder (where the compose files are), run:

```bash
docker-compose -p Arvisan-dev -f docker-compose.yml -f docker-compose.dev.yml up watch
```

This will:

- Build and start the backend, frontend, and Neo4j services.
- Mount code for live development.
- Automatically reload on file changes.

---

### 4B. Run Locally without Docker

1. Make sure your Neo4j database is running (with APOC plugin enabled).
2. Start the backend:

```bash
cd arvisan-backend
npm install
npm run dev
```

3. In a new terminal, start the frontend:

```bash
cd ../arvisan-frontend
npm install
npm run dev
```

You now have:

- Backend server running (typically on `localhost:3000`)
- Frontend UI running (typically on `localhost:5173`)

---

## 🧪 Done!

You’re now running ARViSAN locally. Navigate to [localhost:5173](localhost:5173) and login with the credentials (by default `test_user`, `test_password`). You can parse source code using the dependency parser and upload the generated graph to explore it through the ARViSAN UI.


---
