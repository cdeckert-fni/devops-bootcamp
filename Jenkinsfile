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
        stage('Docker Image Build') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'ECRAccess', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                    sh '''
                        echo ============================
                        echo $AWS_SECRET_ACCESS_KEY 
                        echo $AWS_ACCESS_KEY_ID
                        echo ============================
                        wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
                        dpkg -i ./docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
                        apt-get update
                        apt-get install -y awscli
                        docker build -t workshopuser2:latest .
                        docker tag workshopuser2:latest workshopuser2:${BUILD_NUMBER}
                        docker tag workshopuser2:latest 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser2:latest
                        $(aws ecr get-login --region us-east-1 | sed 's/-e none//g')
                        docker push 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser2:latest
                    '''
                }
            }
        }
    }
}