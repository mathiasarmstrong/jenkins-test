pipeline {
    agent {
      kubernetes {
        defaultContainer 'jnlp'
        label 'kube-label'
        yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: jenkins-node
    image: node:lts
    command:
    - cat
    tty: true

'''
      }
    }
    stages {
        stage('Build') {
            steps {
              container("jenkins-node"){
                sh 'npm install -g yarn'
                sh 'yarn'
              }
            }
        }
        // stage('Test') {
        //     steps {
        //       container("jenkins-node"){
        //         sh 'yarn test'
        //       }
        //     }
        // }
        // stage('Deliver') {
        //     steps {
        //         sh './jenkins/scripts/deliver.sh'
        //         input message: 'Finished using the web site? (Click "Proceed" to continue)'
        //         sh './jenkins/scripts/kill.sh'
        //     }
        // }
    }
}
