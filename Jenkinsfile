pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                tools {
                    jdk 'jdk17'
                    maven 'mvn'
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
                tools {
                    jdk 'jdk17'
                    maven 'mvn'
                }
            steps {
                sh 'mvn deploy'
            }
        }
    }
}
