/*pipeline {
    agent any 
    
    stages { 
        stage('SCM Checkout') {
            steps {
                retry(3) {
                    git branch: 'main', url: 'https://github.com/HGSChandeepa/test-node'
                }
            }
        }
        stage('Build Docker Image') {
            steps {  
                bat 'docker build -t adomicarts/nodeapp-cuban:%BUILD_NUMBER% .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'samin-docker', variable: 'samindocker')]) {
                    script {
                        bat "docker login -u adomicarts -p %samindocker%"
                    }
                }
            }
        }
        stage('Push Image') {
            steps {
                bat 'docker push adomicarts/nodeapp-cuban:%BUILD_NUMBER%'
            }
        }
    }
    post {
        always {
            bat 'docker logout'
        }
    }
}

*/


pipeline{

//can add enviroment variable or manual triggers here
    stages{
        stage("Checkout from the code repo"){
            steps{
                retry(3) {

                git branch : 'main',url : 'https://github.com/Hasindu-1/GitHub-Docker-and-Jenkins-CI-CD-Pipeline.git'
                }
                
            }
        }
        stage("Building Dokcer Image"){
            steps{
                //using bat just beacuse it is windows agent
                //use sh for linux agents
                bat 'docker build -t hasindu1/nodeapp:%BUILD_NUMBER% .'
            }
        }
        stage("login to docker hub"){
            steps{
                withCredentials([string(credentialsId: 'docker-password-test', variable: 'docker-password')]) {
             // some block
            bat 'docker login -u hasindu-1 -p ${docker-password}'
                }
            }

        }stage("Pushing Docker Image  to docker hub "){
            steps{
                bat 'docker push hasindu-1/nodeapp:%BUILD_NUMBER%'
            }
        }



    }
    post{
        always{
            bat 'docker logout'
        }
    }
}
