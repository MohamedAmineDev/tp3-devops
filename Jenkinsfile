pipeline{
  agent any
  tools{
    maven 'maven'
  }
  stages{
    stage("Clean un"){
      steps{
        deleteDir()
      }
    }
    stage("Clone repo"){
      steps{
        sh "git clone https://github.com/MohamedAmineDev/spring-boot-devops-tp3.git "
      }
    }
    stage("Generate backend image"){
      steps{
        dir("spring-boot-devops-tp3"){
          sh "mvn clean install -DskipTests"
          sh "docker build -t web-backend ."
        }
      }
    }
    stage("Run docker compose"){
      steps{
        dir("spring-boot-devops-tp3"){
          sh "docker compose up -d"
        }
      }
    }
  }
}
