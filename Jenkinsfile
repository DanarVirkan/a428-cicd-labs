node {
    checkout scm
    docker.image('node:18.16.0-alpine').inside {
        stage('Build') {
                sh 'node --version'
                sh 'npm install'
            }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
        stage('Deliver') {
            sh './jenkins/scripts/deliver.sh'
            input message: 'Finished using the web site? (Click "Proceed" to continue)'
            sh './jenkins/scripts/kill.sh'
        }
        stage('Manual Approval') {
            echo 'Mock Continous Delivery'
            input(message: "Lanjutkan ke tahap Deploy?")
        }
        stage('Deploy') {
            echo 'Mock Deploy'
            sleep(time: 1, unit: 'MINUTES')
        }
    }
}