pipeline {
    agent any
    
    stages {
        stage('Hello') {
            
            steps {
                echo 'Hello World'
                nodejs('chrisnode') {
                    sh 'npm install'
                }
            }
        }
    }
}