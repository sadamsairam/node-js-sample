pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/sadamsairam/node-js-sample.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Run App') {
            steps {
                sh 'nohup npm start &'
            }
        }
        
       pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sadamsairam/node-js-sample.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t node-app .'
            }
        }

        stage('Docker Run') {
            steps {
                sh '''
                docker stop node-app || true
                docker rm node-app || true
                docker run -d -p 3000:3000 --name node-app node-app
                '''
            }
        }
    }
}
}
