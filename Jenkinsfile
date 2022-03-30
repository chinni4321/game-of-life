pipeline {
agent { label 'master' }

  tools {
    jdk 'Java8'
    maven 'Maven3.3.9'

  }
 stages {
     stage('Git checkout'){
       steps {
          git 'https://github.com/chinni4321/game-of-life.git'
     
       }
    }

     stage('Maven Build'){
       steps {
          sh 'mvn clean install'
     
       }
     }
  }
}
    
