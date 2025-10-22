# 🌌 Solar System API

A lightweight **Node.js** API for exploring solar system data, powered by **MongoDB**, containerized with **Docker**, and deployed through a **Jenkins CI/CD pipeline**.

---

## 📑 Table of Contents
- [🌟 Overview](#-overview)
- [🛠 Prerequisites](#-prerequisites)
- [📂 Project Structure](#-project-structure)
- [🚀 Setup Instructions](#-setup-instructions)
- [🔄 CI/CD Pipeline](#-cicd-pipeline)
- [🔧 Environment Variables](#-environment-variables)
- [▶️ Running the Application](#️-running-the-application)
- [🐳 Docker Image](#-docker-image)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)

---

## 🌟 Overview
The **Solar System API** provides access to rich solar system data stored in a **MongoDB** database.  
It is built with **Node.js**, packaged using **Docker** for portability, and automated through a **Jenkins pipeline** for continuous integration and delivery.

---

## 🛠 Prerequisites
To set up and run this project, ensure you have the following installed:

| Tool | Purpose |
|------|----------|
| 🐋 **Docker** | For building and running containers |
| 🟩 **Node.js** | Version 18 (included in `node:18-alpine3.17`) |
| 🍃 **MongoDB** | For storing solar system data |
| ⚙️ **Jenkins** | CI/CD automation |
| ☁️ **Docker Hub Account** | For pushing and pulling images |
| 🔧 **Git** | For cloning the repository |

---

## 📂 Project Structure
├── Dockerfile # Docker configuration for the Node.js app
├── Jenkinsfile # Jenkins CI/CD pipeline configuration
├── package.json # Node.js dependencies and scripts
├── src/ # Application source code
└── README.md # Project documentation


---

## 🚀 Setup Instructions

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/mohamedbstar413/jenkins-solar-system2.git
cd jenkins-solar-system2

2️⃣ Install Dependencies
npm install

3️⃣ Set Up MongoDB

Run MongoDB locally or in a container:

docker run -d -p 27017:27017 mongo


Then configure MongoDB credentials in your environment or Jenkins pipeline.

4️⃣ Run Locally
npm start


Your API will be accessible at: http://localhost:3000

🔄 CI/CD Pipeline

The Jenkins pipeline automates build, test, and deployment with the following stages:

Pull Code – Clones the repository from GitHub.

Install Dependencies – Executes npm install to set up the environment.

Run Tests – Runs placeholder tests (update with npm test when ready).

Build, Tag, and Push Image –
Builds a Docker image named <DOCKER_USER>/solar-image:latest
and pushes it to Docker Hub using stored credentials.

🧩 Jenkins Configuration

Jenkins node should have the docker agent label.

Add the following credentials:

mongodb → MongoDB username/password

dockerhub → Docker Hub username/password

Install the Node.js plugin and configure a node-js tool inside Jenkins.

🔧 Environment Variables
Variable	Description
MONGO_INITDB_ROOT_USERNAME	MongoDB admin username (from Jenkins credentials)
MONGO_INITDB_ROOT_PASSWORD	MongoDB admin password (from Jenkins credentials)
MONGO_URL	MongoDB connection string (e.g., mongodb://admin:<password>@my-mongo:27017/mydb?authSource=admin)
REPO_URL	GitHub repository URL (https://github.com/mohamedbstar413/jenkins-solar-system2)
DOCKER_CREDS	Docker Hub credentials (username and password)
▶️ Running the Application
🐳 Using Docker

Pull the prebuilt image:

docker pull <DOCKER_USER>/solar-image:latest


Run the container:

docker run -p 3000:3000 -e MONGO_URL=<your-mongo-url> <DOCKER_USER>/solar-image:latest

💻 Running Locally

Set the MongoDB connection string and start the app:

export MONGO_URL="mongodb://localhost:27017/solar"
npm start

🐳 Docker Image

Built using node:18-alpine3.17 and exposes port 3000.

Dockerfile Highlights:

Sets the working directory to /usr/app

Copies and installs dependencies

Copies application source code

Starts the app with npm start

Find the image on Docker Hub:

<DOCKER_USER>/solar-image:latest
