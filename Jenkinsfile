pipeline {
  agent { label 'master' }

  tools {
    jdk 'Java8'
    maven 'Maven3.3.9'
  }
 parameters {
      string(defaultValue: 'master', description: 'Please type any branch name to deploy', name: 'Branch')
 }  

stages {
    stage('Git checkout'){
      steps {
        git branch: '${Branch}',
        url: 'https://github.com/chinni4321/game-of-life.git'
      }
    }
    stage('Maven build'){
      steps {
        sh 'mvn clean install'
      }
    }
 }
}
