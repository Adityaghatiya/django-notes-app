@Library("shared-library") _
pipeline {
    agent { label 'dhapu' }

    stages {
        
        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Clone') {
            steps {
                script{
                    clone('https://github.com/Adityaghatiya/django-notes-app', 'main')
                }
            }
        }

        stage('Build') {
            steps {
                script{
                    build("notes-app",'latest','cloudhero')
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
               script{
                   push("notes-app", "latest", "cloudhero")
               }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying container'
                sh 'sudo docker compose down && sudo docker compose up -d'
            }
        }
        stage('bye') {
            steps {
               echo 'Bye Bye Aditya'
            }
        }
    }
}
