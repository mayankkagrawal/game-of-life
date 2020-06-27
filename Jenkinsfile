pipeline {
  agent any
  stages {
    stage ("git checkout"){
        steps {
            git credentialsId: 'github', url: 'https://github.com/mayankkagrawal/game-of-life'
           }
        }
    stage ("Maven build"){
        steps {
           sh  "mvn clean package"
        }
      }
    stage ("store artficat"){
      steps {
       nexusPublisher nexusInstanceId: '1234', nexusRepositoryId: 'releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'gameoflife-web/target/gameoflife.war']], mavenCoordinate: [artifactId: 'gameoflife', groupId: 'com.wakaleo.gameoflife', packaging: 'war', version: '1.0']]] 
      }
    }
    stage("deploy"){
      steps {
        sh label: '', script: 'sudo docker cp gameoflife-web/target/gameoflife.war maven:/opt/tomcat/webapps'
      }
      }
     }
  }
