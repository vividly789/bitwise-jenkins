pipeline {
  agent {
    docker {
      image 'maven:3.3.9-jdk-8'
      args '-v /Users/bitwiseman/man/.m2:/root/.m2'
    }

  }
  stages {
    stage('Initalize') {
      steps {
        echo 'This is minimal pipeline!'
        sh '''        
echo PATH = ${PATH}








echo M2_HOME = ${M2_HOME}
mvn clean'''
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true install'
      }
    }

    stage('Report') {
      steps {
        junit 'target/surefire-reports/**/*.xml'
        archiveArtifacts 'target/*.jar.target/*.hpi'
      }
    }

  }
}