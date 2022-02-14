def HOME_DIR="/home/jenkins-agent"

pipeline{
    agent {
        node {
            label 'webserver'
        }
    }

    stages {
        stage("Prepare"){
            steps{
                echo "Setting up..."
                echo "Checking node and npm"
                sh "node -v"
                sh "npm -v"
                echo "Stop all existing process"
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'npm install --save'
                sh 'export NODE_ENV=production'
                sh 'export NODE_PORT=8080'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh "npm test"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh "npm start"
            }
        }
    }
}