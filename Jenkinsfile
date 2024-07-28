pipeline {
    agent any

    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk17'
    }

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
