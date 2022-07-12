#!groovy

pipeline {
  agent none
  stages {
  /*  stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    } */
     stage("Git Clone"){

        git credentialsId: '', url: 'https://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@github.com/stefanmucha/spring-petclinic'
    }

     stage('Gradle Build') {

       sh './gradlew build'

    }

    
    
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build --no-cache -t muchast2/spring-petclinic:latest .'
       // sh 'docker stop muchast2/spring-petclinic:latest'
        sh 'docker run -p 8081:8080 muchast2/spring-petclinic:latest &'
        sh 'docker images --quiet --filter=dangling=true | xargs --no-run-if-empty docker rmi'
      }
    }
    
}
}
