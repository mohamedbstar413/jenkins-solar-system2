pipeline {
    agent { label 'docker' }
    environment {
        MONGO_CREDS = credentials('mongodb')

        MONGO_INITDB_ROOT_USERNAME = "$MONGO_CREDS_USR"
        MONGO_INITDB_ROOT_PASSWORD = "$MONGO_CREDS_PSW"

        MONGO_URL = "mongodb://admin:$MONGO_INITDB_ROOT_PASSWORD@my-mongo:27017/mydb?authSource=admin"

        REPO_URL = 'https://github.com/mohamedbstar413/jenkins-solar-system2'

        DOCKER_CREDS = credentials('dockerhub')
    }

    tools {
        nodejs 'node-js'
    }

    stages {
        stage('pull code') {
            steps {
                git "${env.REPO_URL}"
            }
        }
        stage('install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('run tests') {
            steps {
                sh 'echo testing...'
            //sh 'npm test'
            }
        }

        stage('build, tag and push the image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh '''
                echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                docker build -t $DOCKER_USER/solar-image:latest .
                docker push $DOCKER_USER/solar-image:latest
            '''
                }
            }
        }
    }
}

