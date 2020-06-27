pipeline {
  agent any
  stages {
    stage ("git checkout"){
        steps {
            git credentialsId: 'github', url: 'https://github.com/mayankkagrawal/game-of-life'
           }
        }
    stage (Maven build"){
        steps {
           sh  "mvn clean package"
        }
      }
     }
  }
