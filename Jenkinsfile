pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
        ENV = 'test'
    }
    stages {
        stage('Build') {
            steps {
                sh "npm install -g yarn"
                sh 'yarn'
            }
        }
        stage('Test') {
            steps {
                sh 'jest'
            }
        }
        // stage('Deliver') {
        //     steps {
        //         sh './jenkins/scripts/deliver.sh'
        //         input message: 'Finished using the web site? (Click "Proceed" to continue)'
        //         sh './jenkins/scripts/kill.sh'
        //     }
        // }
    }
}
