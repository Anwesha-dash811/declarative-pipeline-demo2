pipeline {
  agent any
  environment {
    RELEASE='20.04'
  }
  stages {
    stage('Build') {
      environment {
        LOG_LEVEL="INFO"
      }
      steps {
        echo "Building Release ${RELEASE} with log level ${LOG_LEVEL}"
        sh '''
         echo "running a shell script"
         chmod +x test.sh
         ./test.sh
        
        '''
      }
    }
   stage('Test') {
     steps {
       echo "Testing Release ${RELEASE} "
       writeFile file: 'test-results.txt', text: 'passed'
      }
    }
  }
    post {
      success {
        archiveArtifact 'test-results.txt'
      }
    }
}
