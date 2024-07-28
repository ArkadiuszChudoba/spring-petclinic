pipeline {
    agent any

    tools {
        jdk 'jdk-apple'
        maven 'mvn'
    }



    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'java --version'
                sh 'echo "$JAVA_HOME"'
                sh 'JAVA_HOME=/Users/achudoba/.jenkins/tools/hudson.model.JDK/jdk17-2/jdk-17.0.2; mvn clean install'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
            steps {
                sh 'mvn deploy'
            }
        }
    }
}
