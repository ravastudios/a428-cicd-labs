pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }    
    stages {
        stage('Build local') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test local') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver local') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the website? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
