pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage("Clean up"){
            steps{
                deleteDir()
            }
        }
        stage("Clone repo"){
            steps{
                sh "git clone https://github.com/MohamedAmineDev/tp3-devops.git"
            }
        }
        stage("Generate docker image"){
            steps{
                dir("tp3-devops"){
                    sh "mvn clean install"
                    sh "docker build -t new-backend ."
                }
            }
        }
        stage("Run docker compose"){
            steps{
                dir("tp3-devops"){
                    sh "docker compose up -d "
                }
            }
        }
    }
}
