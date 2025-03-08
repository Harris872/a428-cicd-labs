async function fetchData(){
    console.log("Fetching data...");
    await sleep(60000);
    console.log("Data fetched delay.")
}
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
             //input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
             //sh './jenkins/scripts/kill.sh'
             fetchData();
        }
    }
}
