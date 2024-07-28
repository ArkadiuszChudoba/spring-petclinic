pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'mvn clean install'
            }
        }
        stages {
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
}
