@Library("Shared") _
pipeline {
    
    agent { label "anshu"}
    
    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script {
                    clone("https://github.com/LondheShubham153/django-notes-app.git","main")
                }
            }
        }
        stage("Build") {
            steps {
                script {
                    docker_build("notes-app","latest","sudhanshumehta")
                }
            }
        }
        stage("Push to DockerHub") {
            steps {
                echo "We push image to docker hub"
                script {
                    docker_push("notes-app","latest","sudhanshumehta")
                }
            }
        }
        stage("Deploy") {
            steps {
                echo "Deployment Process start here"
                sh "docker compose up -d"
            }
        }
    }
}
