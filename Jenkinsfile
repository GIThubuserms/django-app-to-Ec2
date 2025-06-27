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
            docker-build("djangoapp1")
        }
      }
    }
    stage("Run") {
      steps {
       script{
           docker-run("djangoapp1","8000","mycon1")
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
          sh "docker image tag djangoapp1:latest murtaza0318/djangoapp1:latest"
          sh "docker push murtaza0318/djangoapp1:latest"
          echo "Deployed"
        }
      }
    }
  }
}
