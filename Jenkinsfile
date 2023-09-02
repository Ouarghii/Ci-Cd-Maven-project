
pipeline {
  agent any
  tools {
    maven 'maven-3.9'
  }
  stages {
    stage("build jar") {
        steps {
           script {
             echo "Building app ..."
             sh 'mvn package'
           }
         }
      }
    stage("build image") {
        steps {
           script {
             echo "Building docker image ..."
             withCredentials([usernamePassword(credentialsId: 'Raslen',passwordVariable:'warghui110', usernameVariable: 'Raslen')]) {
                sh 'docker build -t raslenouarghi/maven-app .'
                sh "echo $PASS | docker login -u $USER --password-stdin "
                sh 'docker push raslenouarghi/maven-app '
             }
           }
         }
      }

      stage("deploy") {
         steps {
          script {
            echo "Deploying app ..."
            }
         }
      }
  }
}
