pipeline {
    agent {
      kubernetes {
        defaultContainer 'jnlp'
        yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: node
    image: node:lts
    command:
    - npm install -g yarn
    tty: true
"""
      }
    }
    environment {
        CI = 'true'
        ENV = 'test'
    }
    stages {
        stage('Build') {
            steps {
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
