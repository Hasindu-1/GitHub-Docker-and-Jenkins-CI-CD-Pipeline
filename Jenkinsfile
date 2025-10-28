pipeline {
    agent any
    //can add environment variable or manual triggers here
    stages {
        stage("Checkout from the code repo") {
            steps {
                retry(3) {
                    git branch: 'main', url: 'https://github.com/Hasindu-1/GitHub-Docker-and-Jenkins-CI-CD-Pipeline.git'
                }
            }
        }

        stage("Building Docker Image") {
            steps {
                //using bat just because it is windows agent
                //use sh for linux agents
                bat 'docker build -t hasindu1/nodeapp:%BUILD_NUMBER% .'
            }
        }

     
        
        stage("Login to Docker Hub") {
            steps {
                withCredentials([string(credentialsId: 'docker-youtube-id', variable: 'docker-youtube')]) {
                    // ✅Space after echo + variable name changed
                    bat """
                        echo %docker-youtube% | docker login -u hasindu1 --password-stdin
                    """
                }
            }
        }


        stage("Pushing Docker Image to Docker Hub") {
            steps {
                bat 'docker push hasindu1/nodeapp:%BUILD_NUMBER%'
            }
        }
    }

    post {
        always {
            bat 'docker logout'
        }
    }
}
