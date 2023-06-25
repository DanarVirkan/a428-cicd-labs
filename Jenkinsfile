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
        stage('Manual Approval') {
            input(message: "Lanjutkan ke tahap Deploy?")
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            input message: 'Finished using the web site? (Click "Proceed" to continue)'
            sh './jenkins/scripts/kill.sh'
            sleep(time: 1, unit: 'MINUTES')
        }
    }
}