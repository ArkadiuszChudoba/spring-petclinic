pipeline {
    agent any

    tools {
        jdk 'jdk17'
        maven 'mvn'
    }



    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'java --version'
                sh 'echo "$JAVA_HOME"'
                sh 'mvn clean install'
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
