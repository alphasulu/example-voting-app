pipeline {
    agent {
        docker {
            image 'python:2.7.16-slim' 
            args '--user root'
         }
    }
    stages {
        stage('Build') {
            steps {
                  sh "pip install -r vote/requirements.txt"
            }
        }
        stage('Test') {
            steps {
                dir('vote') {
                     sh 'nosetests -v'
                }
            }
        }
    }
}
