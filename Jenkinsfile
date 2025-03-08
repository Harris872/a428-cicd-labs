node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000'){
        stage('Build') {
            checkout scm
            echo 'push untuk user dicoding'
            sh 'npm install'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
        stage('Manual Approval') {
            input message: 'Lanjutkan ke tahap Deploy? (Klik "Proceed" untuk lanjut deploy)' 
        }

        stage('Deploy') {
             sh './jenkins/scripts/deliver.sh'
             sh sleep 60
             //input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
             //sh './jenkins/scripts/sleep.sh'
             sh './jenkins/scripts/kill.sh'
        }
    }
}
