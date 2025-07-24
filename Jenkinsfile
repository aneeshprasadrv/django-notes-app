@Library('Shared') _
pipeline {
    agent {label 'vinod'}
    
stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps{
                script{
                    clone("https://github.com/aneeshprasadrv/django-notes-app.git", "main")
                    echo 'code cloned successfully done'
                }
            }
        }
        stage("build") {
            steps{
                script{
                docker_build("notesapp", "latest", "aneeshprasad36")
                }
            }
        }
        stage("Push to Dockerhub") {
            steps{
                script{
                push_dockerhub("notesapp", "latest", "aneeshprasad36")
                }
            }
        }

         stage("deploy") {
            steps{
                echo 'this is deploying the code'
                sh 'docker-compose down && docker-compose up -d'
            }
        }
    }
}
