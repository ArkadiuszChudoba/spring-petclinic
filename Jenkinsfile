pipeline {
    agent any

    tools {
        jdk 'jdk17'
        maven 'mvn'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    env.JAVA_HOME="${tool 'jdk17'}"
                    env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
                }
                echo 'Building..'
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
