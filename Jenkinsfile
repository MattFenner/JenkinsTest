pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''mkdir -p artifacts
cd artifacts
echo "hello world" > test.txt'''
      }
    }
    stage('Test') {
      steps {
        parallel(
          "manual": {
            input(message: 'good?', id: 'good', ok: 'Yes')
            
          },
          "auto": {
            sh '''cd artifacts
$result = $(cat test.txt) == "hello world"
exit $result'''
            
          }
        )
      }
    }
    stage('Deploy') {
      steps {
        input(message: 'deploy?', id: 'deploy', ok: 'do it!')
        sh 'echo "deploying!"'
      }
    }
  }
}