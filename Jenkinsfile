pipeline {
    agent any

    tools {
        jdk 'jdk17'
        maven 'mvn'
    }

    env.JAVA_HOME="${tool 'jdk17'}"
    env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"

    stages {
        stage('Build') {
            steps {
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
