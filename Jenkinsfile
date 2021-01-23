pipeline {
  agent any
  
  tools {
    Nodejs
  }
  
  stages {
    stage("build") {
      when {
        changeset "**/result/**"
      }
      
      steps {
        echo 'build the result nodeJs app'
        dir('result') {
          sh 'npm install'
        }
      }
    }
   
   stage("test") {
    when {
      changeset "**/result/**"
    }
    
    steps {
      echo 'run the test'
      dir('result') {
        sh 'npm test'      
      }
    }
   }
  }
}
