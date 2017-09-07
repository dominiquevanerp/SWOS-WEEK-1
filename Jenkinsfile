pipeline {
  agent any
  tools { 
      maven 'Maven 3.5.0' 
      jdk 'jdk8' 
  }
  stages {
    stage('Initialize') {
      steps {
        sh 'mvn clean'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true install'
      }
    }
    stage('Report') {
      steps {
        junit 'target/surefire-reports/** /*.xml'
        archiveArtifacts 'target/*.jar,target/*.hpi'
      }
    }
  }
  environment {
    Maven = '3.5.0'
  }
}
