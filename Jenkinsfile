pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2.7.16-slim' 
                    args '--user root'
                }
            }
             when {
                changeset "**/vote/**"
            }
            steps {
                dir("vote") {
                    sh "pip install -r requirements.txt"
                }
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'python:2.7.16-slim' 
                    args '--user root'
                }
            }
             when {
                changeset "**/vote/**"
            }
            steps {
                dir('vote') {
                    sh "pip install -r requirements.txt"
                    sh 'nosetests -v'
                }
            }
        }
    }
}
