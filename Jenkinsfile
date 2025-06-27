@Library("FirstLib") _
pipeline {
  agent { label "agent1" }
  stages {
    stage("hello") {
      steps {
        script{
         hello()   
        }
      }
    }
    stage("clone"){
        steps {
            script {
                clone("https://github.com/GIThubuserms/django-app-to-Ec2.git","main")
            }
        }
    }
    stage("build") {
      steps {
        script{
            docker-build("django-app-1")
        }
      }
    }
    stage("Run") {
      steps {
       script{
           docker-run("django-app-1","8000","mycon1")
       }
      }
    }
    stage("deploy") {
      steps {
        echo "Deploying"
        withCredentials([usernamePassword(
          credentialsId: "DockerHubCred",
          passwordVariable: "DockerHubpass",
          usernameVariable: "DockerHubuser"
        )]) {
          sh "docker login -u $DockerHubuser -p $DockerHubpass"
          sh "docker image tag mydjangoimage:latest murtaza0318/djangonotesimage:latest"
          sh "docker push murtaza0318/djangonotesimage:latest"
          echo "Deployed"
        }
      }
    }
  }
}
