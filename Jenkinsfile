pipeline {
    
    agent { label 'master' }


environment {

      sonar_url = 'http://172.31.12.92:9000'
      sonar_username = 'admin'
      sonar_password = 'admin'
      nexus_url = '172.31.12.92:8081'
      artifact_version = '4.0.0'

 }

    tools {
    jdk 'Java8'
    maven 'Maven3.3.9'

  }

    stages {
        
        stage('Git Clone') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/chinni4321/game-of-life.git'

            }

        }
        stage('Maven build') {
            steps {
                // Get some code from a GitHub repository
                sh  'mvn clean install -U -Dmaven.test.skip=true'

            }
        }

     stage ('Sonarqube Analysis'){
           steps {
           withSonarQubeEnv('sonarqube') {
           sh '''
           mvn -e -B sonar:sonar -Dsonar.java.source=1.8 -Dsonar.host.url="${sonar_url}" -Dsonar.login="${sonar_username}" -Dsonar.password="${sonar_password}" -Dsonar.sourceEncoding=UTF-8
           '''
           }
         }
      }
    stage ('Publish Artifact') {
        steps {
          nexusArtifactUploader artifacts: [[artifactId: 'gameoflife', classifier: '', file: "/var/lib/jenkins/workspace/pipeline/gameoflife-build/target/gameoflife-build-1.0-SNAPSHOT.jar", type: 'jar']], credentialsId: '4b712aef-e7f0-4550-aa66-bbb4be01c50d', groupId: 'com.wakaleo.gameoflife', nexusUrl: "${nexus_url}", nexusVersion: 'nexus3', protocol: 'http', repository: 'release', version: "${artifact_version}"
         archiveArtifacts '**/*.jar'
        }
      }
      
    }
}
