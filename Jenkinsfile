pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        parallel(
          "build a": {
            sleep 30
            
          },
          "build b": {
            sleep 10
            
          }
        )
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test": {
            echo 'printing a message'
            
          },
          "": {
            input(message: 'good?', id: 'good', ok: 'OK')
            
          }
        )
      }
    }
    stage('Deploy') {
      steps {
        sh '''echo hi

sleep 30s'''
      }
    }
  }
}