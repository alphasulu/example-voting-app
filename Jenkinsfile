pipeline {
    agent none
    stages {
        stage('Vote Build') {
            agent {
                docker {
                    image 'python:2.7.16-slim' 
                    args '--user root'
                }
            }
            steps {
                  sh "pip install -r vote/requirements.txt"
            }
        }
        stage('Vote Test') {
            agent {
                docker {
                    image 'python:2.7.16-slim' 
                    args '--user root'
                }
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
