Solar System API
A Node.js application for exploring solar system data, containerized with Docker and deployed via a Jenkins CI/CD pipeline.
Table of Contents

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

Overview
This project is a Node.js-based API for accessing solar system data, stored in a MongoDB database. It is containerized using Docker and automated through a Jenkins pipeline for building, testing, and deploying to Docker Hub.
Prerequisites

Docker: To build and run the containerized application.
Node.js: Version 18 (provided by the node:18-alpine3.17 Docker image).
MongoDB: A running MongoDB instance for data storage.
Jenkins: For CI/CD pipeline execution.
Docker Hub Account: For pushing and pulling Docker images.
Git: For cloning the repository.

Project Structure
├── Dockerfile          # Docker configuration for the Node.js app
├── Jenkinsfile         # Jenkins pipeline for CI/CD
├── package.json        # Node.js dependencies and scripts
├── src/                # Source code for the application
└── README.md           # Project documentation

Setup Instructions

Clone the Repository:
git clone https://github.com/mohamedbstar413/jenkins-solar-system2.git
cd jenkins-solar-system2


Install Dependencies:Ensure Node.js is installed, then run:
npm install


Set Up MongoDB:

Ensure a MongoDB instance is running (e.g., via Docker: docker run -d -p 27017:27017 mongo).
Configure credentials in your environment or CI/CD system.


Run Locally:
npm start

The application will be available at http://localhost:3000.


CI/CD Pipeline
The Jenkins pipeline automates the build, test, and deployment process. It includes the following stages:

Pull Code: Clones the repository from GitHub.
Install Dependencies: Installs Node.js dependencies using npm install.
Run Tests: Executes tests (currently a placeholder; replace with npm test for actual test scripts).
Build, Tag, and Push Image:
Builds a Docker image tagged as <DOCKER_USER>/solar-image:latest.
Pushes the image to Docker Hub using provided credentials.



Jenkins Setup

Ensure the Jenkins server has the docker agent label.
Configure credentials in Jenkins:
mongodb: MongoDB username and password.
dockerhub: Docker Hub username and password.


Install the Node.js plugin in Jenkins and configure the node-js tool.

Environment Variables
The application and pipeline rely on the following environment variables:



Variable
Description



MONGO_INITDB_ROOT_USERNAME
MongoDB admin username (from Jenkins credentials)


MONGO_INITDB_ROOT_PASSWORD
MongoDB admin password (from Jenkins credentials)


MONGO_URL
MongoDB connection string


REPO_URL
GitHub repository URL


DOCKER_CREDS
Docker Hub credentials (username and password)


Running the Application

Using Docker:Pull the image from Docker Hub:
docker pull <DOCKER_USER>/solar-image:latest

Run the container:
docker run -p 3000:3000 -e MONGO_URL=<your-mongo-url> <DOCKER_USER>/solar-image:latest


Locally:Set the MONGO_URL environment variable and run:
npm start



Docker Image
The Docker image is built from the node:18-alpine3.17 base image and exposes port 3000. The Dockerfile:

Sets the working directory to /usr/app.
Copies package.json and installs dependencies.
Copies the application code.
Runs npm start to launch the app.

The image is available on Docker Hub as <DOCKER_USER>/solar-image:latest.
Contributing

Fork the repository.
Create a feature branch (git checkout -b feature/your-feature).
Commit your changes (git commit -m "Add your feature").
Push to the branch (git push origin feature/your-feature).
Open a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.
