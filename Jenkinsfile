node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000'){
        stage('Build') {
            sh 'npm install'
        }
        stage('Test') {
            echo 'test'
            sh './jenkins/scripts/test.sh'
        }
    }
}