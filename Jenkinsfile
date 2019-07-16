pipeline {
    agent {
      kubernetes {
        containerTemplate {
          name 'node'
          image 'node:lts'
          args '-p 3000:3000'
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
