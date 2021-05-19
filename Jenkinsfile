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
                echo 'Building stuff'
                nodejs('chrisnode') {
                    sh 'npm test'
                }
            }
        }
    }
}