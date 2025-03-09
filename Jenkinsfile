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
           def dockerCmd = 'docker run  -p 3000:3000 -d Harris/react-app:latest'
           sshagent(['ec2-server-key']) {
           sh "ssh -o StrictHostKeyChecking=no ec2-user@13.250.25.130 ${dockerCmd}"
           } 
            //  sh './jenkins/scripts/deliver.sh'
            //  sh 'sleep 60'
            //  sh './jenkins/scripts/kill.sh'
        }
    }
}
