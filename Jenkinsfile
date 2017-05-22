pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        parallel(
          "Initialize": {
            echo 'Initializing 1'
            
          },
          "Initialize 2": {
            echo '2'
            
          }
        )
      }
    }
    stage('Build') {
      steps {
        echo 'Build'
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test": {
            echo 'Test'
            
          },
          "Test 2": {
            echo 'Test2'
            
          },
          "Static Code Analysis": {
            echo 'Code Analyzed'
            
          }
        )
      }
    }
    stage('Ready to Deploy') {
      steps {
        input(message: 'Should I deploy?', id: '_ready', ok: 'Go Ahead')
        slackSend 'Ready to deploy ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deployed'
      }
    }
  }
}