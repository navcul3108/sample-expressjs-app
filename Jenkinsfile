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
                sh "node -v"
                sh "npm -v"
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'npm install --save'
                sh 'export NODE_ENV=production'
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