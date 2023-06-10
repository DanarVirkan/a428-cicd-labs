node {
    stage('Build') {
        docker.image('node:18.16.0-alpine').inside("-p 3000:3000 --network jenkins") {
            sh 'node --version'
            sh 'npm install'
        }
    }
    stage('Test') {
        sh './jenkins/scripts/test.sh'
    }
    stage('Deliver') {
        sh './jenkins/scripts/deliver.sh'
        input message: 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
    }
}