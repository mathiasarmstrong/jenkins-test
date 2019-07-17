pipeline {
    agent {
      kubernetes {
        defaultContainer 'jnlp'
        yamlFile 'KubernetesPod.yaml'
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
        stage('Test') {
            steps {
              container("jenkins-node"){
                sh 'yarn test'
              }
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
