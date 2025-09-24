pipeline{
    agent {label 'docker'}
}

environment{
    MONGO_URL="mongodb://admin:secret@my-mongo:27017/mydb?authSource=admin"
    MONGO_USERNAME=admin
    REPO_URL=""
}

tools{
    nodejs 'node-js'
}

stages{
    stage('pull code'){
        steps{
            git branch: 'main', url: "${env.MONGO_URL}"
        }
    }
    stage('test code'){
        steps{
            sh '''

            '''
        }
    }
    stage('build the image'){
        steps{
            sh 'docker build -t solar-image .'
        }
    }
    stage('run the image'){
        steps{
            sh '''
                docker 
            '''
        }
    }
}