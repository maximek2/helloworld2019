pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
      stage('Build'){
        steps {
          echo "Build step"
          sh 'mvn clean'
          sh 'mvn install'
          sh 'mvn package'
        }
     
     
      }
        stage('test '){
        steps {
          echo "test step"
          sh 'mvn test'


        }
     
     
      }
        stage('deploy'){
        steps {
          sshPublisher(publishers: [sshPublisherDesc(configName: 'docker-hosts', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''docker build -t webapp:v1.0.; docker tag webapp:v1.0 maximek2/webapp:v1.0 ; docker push maximek2/webapp:v1.0
''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
          sleep 2
        }
     
     
      }
   
    }

}

