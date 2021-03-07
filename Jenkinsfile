pipeline {
    agent none
    stages {
        stage("result Build") {
            agent {
                docker {
                    image 'node:15.11-slim'
                    args '--user root'
                }
            }
            steps {
                echo 'build the result nodeJs app'
                dir('result') {
                    sh 'npm install'
                }
            }
        }
    
        stage("result test") {
            agent {
                docker {
                    image 'node:15.11-slim'
                    args '--user root'
                }
            }
            steps {
            echo 'run the test'
                dir('result') {
                    sh 'npm install'
                    sh 'npm test'      
                }
            }
        }
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
