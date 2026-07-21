pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker Image...'
                bat 'docker build -t website:v1 .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Test Job...'
                build job: 'Push-to-Test'
            }
        }

        stage('Production') {
            when {
                branch 'master'
            }
            steps {
                echo 'Running Production Job...'
                build job: 'Push-to-Prod'
            }
        }
    }
}