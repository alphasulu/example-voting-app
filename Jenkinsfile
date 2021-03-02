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
        stage('Package Docker Image') {
            agent any
            when {
                changeset "**/vote/**"
            }
            steps{
                echo 'Packaging worker app with docker'
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
                        def workerImage = docker.build("initcron/vote:v${env.BUILD_ID}", "./vote")
                        workerImage.push()
                        workerImage.push("${env.BRANCH_NAME}")
                        workerImage.push("latest")
                    }
                }
            }
        }
    }
}
