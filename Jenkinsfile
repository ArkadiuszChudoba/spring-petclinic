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
                sh 'JAVA_HOME="$JAVA_HOME"; mvn clean install'
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
