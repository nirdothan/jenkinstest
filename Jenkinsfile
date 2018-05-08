pipeline {
  agent any
  stages {
    stage('git') {
      agent any
      environment {
        myvar = 'nir'
      }
      steps {
        git(url: 'https://github.com/kelseyhightower/nocode.git', branch: 'master', credentialsId: 'nird')
        sh '''echo "NIRNIRNIR"
ls -l
echo "my location"
pwd'''
      }
    }
    stage('env') {
      parallel {
        stage('env') {
          steps {
            sh '''ls -l
echo "my location"
pwd'''
          }
        }
        stage('parallel') {
          steps {
            echo 'parallel step'
            sh 'pwd'
          }
        }
      }
    }
    stage('try') {
      steps {
        echo 'dummyset ${myvar}'
      }
    }
  }
  parameters {
    choice(choices: '''proj1
proj2''', description: '', name: 'REQUESTED_ACTION')
  }
}