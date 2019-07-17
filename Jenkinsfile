pipeline {
    agent {
      kubernetes {
        cloud "kubernetes"
        containerTemplate {
          name 'node'
          image 'node:lts'
          ttyEnabled true
          command 'cat'
        }
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
                sh 'yarn test'
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
