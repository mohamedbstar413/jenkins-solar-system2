🌌 Solar System API
A lightweight Node.js API for exploring solar system data, powered by MongoDB, containerized with Docker, and deployed via a Jenkins CI/CD pipeline.

📑 Table of Contents

Overview
Prerequisites
Project Structure
Setup Instructions
CI/CD Pipeline
Environment Variables
Running the Application
Docker Image
Contributing
License


🌟 Overview
The Solar System API provides access to solar system data stored in a MongoDB database. It is built with Node.js, containerized using Docker for easy deployment, and automated through a Jenkins pipeline for continuous integration and delivery.

🛠 Prerequisites
To set up and run this project, ensure you have:

Docker: For building and running containers.
Node.js: Version 18 (included in node:18-alpine3.17 Docker image).
MongoDB: A running MongoDB instance (local or containerized).
Jenkins: For running the CI/CD pipeline.
Docker Hub Account: For pushing/pulling images.
Git: For cloning the repository.


📂 Project Structure
├── Dockerfile          # Docker configuration for the Node.js app
├── Jenkinsfile         # Jenkins CI/CD pipeline configuration
├── package.json        # Node.js dependencies and scripts
├── src/                # Application source code
└── README.md           # This documentation


🚀 Setup Instructions

Clone the Repository:
git clone https://github.com/mohamedbstar413/jenkins-solar-system2.git
cd jenkins-solar-system2


Install Dependencies:
npm install


Set Up MongoDB:

Run a MongoDB instance (e.g., via Docker):docker run -d -p 27017:27017 mongo


Configure MongoDB credentials in your environment or CI/CD system.


Run Locally:
npm start

The API will be accessible at http://localhost:3000.



🔄 CI/CD Pipeline
The Jenkins pipeline automates the build, test, and deployment process with the following stages:

Pull Code: Clones the repository from GitHub.
Install Dependencies: Runs npm install to set up Node.js dependencies.
Run Tests: Executes tests (currently a placeholder; update with npm test for actual tests).
Build, Tag, and Push Image:
Builds the Docker image as <DOCKER_USER>/solar-image:latest.
Pushes the image to Docker Hub using credentials.



Jenkins Configuration

Ensure the Jenkins server has the docker agent label.
Add credentials in Jenkins:
mongodb: MongoDB username and password.
dockerhub: Docker Hub username and password.


Install the Node.js plugin and configure the node-js tool in Jenkins.


🔧 Environment Variables



Variable
Description



MONGO_INITDB_ROOT_USERNAME
MongoDB admin username (from Jenkins credentials)


MONGO_INITDB_ROOT_PASSWORD
MongoDB admin password (from Jenkins credentials)


MONGO_URL
MongoDB connection string (e.g., mongodb://admin:<password>@my-mongo:27017/mydb?authSource=admin)


REPO_URL
GitHub repository URL (https://github.com/mohamedbstar413/jenkins-solar-system2)


DOCKER_CREDS
Docker Hub credentials (username and password)



▶️ Running the Application
Using Docker

Pull the image from Docker Hub:docker pull <DOCKER_USER>/solar-image:latest


Run the container:docker run -p 3000:3000 -e MONGO_URL=<your-mongo-url> <DOCKER_USER>/solar-image:latest



Locally
Set the MONGO_URL environment variable and run:
npm start


🐳 Docker Image
The Docker image is built using the node:18-alpine3.17 base image and exposes port 3000. The Dockerfile:

Sets the working directory to /usr/app.
Copies package.json and installs dependencies.
Copies the application code.
Runs npm start to start the API.

Find the image on Docker Hub: <DOCKER_USER>/solar-image:latest.

🤝 Contributing
We welcome contributions! To get started:

Fork the repository.
Create a feature branch:git checkout -b feature/your-feature


Commit your changes:git commit -m "Add your feature"


Push to the branch:git push origin feature/your-feature


Open a pull request.


📜 License
This project is licensed under the MIT License. See the LICENSE file for details.
