pipeline{
    agent {label 'docker'}
}

environment{
    MONGO_URL="mongodb://admin:secret@my-mongo:27017/mydb?authSource=admin"
    MONGO_CREDS=credentials('mongodb')
    
    MONGO_INITDB_ROOT_USERNAME=$MONGO_CREDS_USR
    MONGO_INITDB_ROOT_PASSWORD=$MONGO_CREDS_PSW

    REPO_URL="https://github.com/mohamedbstar413/jenkins-solar-system2"

    DOCKER_CREDS = credentials('dockerhub')
}

tools{
    nodejs 'node-js'
}

stages{
    stage('pull code'){
        steps{
            git branch: 'main', url: "${env.REPO_URL}"
        }
    }
    stage('install dependencies'){
        steps{
            sh 'npm install'
        }
    }

    stage('run tests'){
        steps{
            sh 'echo testing...'
            sh 'npm test'
        }
    }
    
    stage('build, tag and push the image'){
        steps{
            sh 'docker build -t solar-image'
            sh "echo $DOCKER_CREDS_PSW | docker login -u $DOCKER_CREDS_USR --password-stdin"
            sh 'docker tag solar-image bstar999/solar-image:latest'
            sh 'docker push solar-image'
            sh 'echo pushed image.'
        }
    }
    
}