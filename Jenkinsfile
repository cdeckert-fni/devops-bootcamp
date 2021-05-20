pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building stuff'
                nodejs('chrisnode') {
                    sh 'npm install'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing stuff'
                nodejs('chrisnode') {
                    sh 'npm test'
                }
            }
        }
        stage('Sonar') {
            steps {
                echo 'Scanning stuff'
                nodejs('chrisnode') {
                    sh 'npm test'
                }
            }
        }
    }
}