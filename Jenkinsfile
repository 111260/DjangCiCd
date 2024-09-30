@Library("Shared") _
pipeline {
    agent { label "afshal" }

    stages {
        stage('hello') {
            steps {
                script {
                    hello() // Assuming a hello() function exists in the shared library
                }
            }
        }

        stage('Code') {
            steps {
                script {
                    clone("https://github.com/111260/DjangCiCd.git", "main") // Cloning the repository
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    docker_build("notes-app", "latest", "muhammadafshalsajid") // Building the Docker image
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the code' // You can add specific test steps if needed
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker_push("notes-app", "latest", "muhammadafshalsajid") // Pushing to DockerHub
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the code'
                sh "docker compose down && docker compose up -d" // Running Docker Compose to deploy
            }
        }
    }
}

