pipeline {

    agent {
        docker {
            image 'node:18'
            args '-u root'
        }
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run App') {
            steps {
                sh 'node app.js'
            }
        }

        stage('Show Date') {
            steps {
                sh 'date'
            }
        }

        stage('Create Artifact') {
            steps {
                sh '''
                apt-get update
                apt-get install -y zip
                zip app.zip *
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'app.zip'
            }
        }
    }
}
