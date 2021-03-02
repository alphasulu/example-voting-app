pipeline {
    agent any
    stages {
        agent {
            docker {
                image 'python:2.7.16-slim' 
                args '--user root'
                }
        }
        stage('Build') {
             when {
                changeset "**/vote/**"
            }
            steps {
                  sh "pip install -r vote/requirements.txt"
            }
        }
        stage('Test') {
             when {
                changeset "**/vote/**"
            }
            steps {
                dir('vote') {
                     sh 'nosetests -v'
                }
            }
        }
    }
}
