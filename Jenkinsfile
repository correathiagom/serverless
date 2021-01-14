pipeline {
  agent {
    label 'aerolito-pipeline'
  }  
  stages {
    stage ('Config Environment') {
      when {
        branch "dev"
      }
      steps {
        sh 'yarn install'
      }
    }
    stage('Compile') {
      when {
        branch "dev"
      }
      steps {
        sh 'npm run compile:public'
      }
    }
    stage('Deploy') {
      when {
        branch "dev"
      }
      steps {
        withAWS(credentials:"aerolito-dev"){
          sh 'serverless deploy --stage dev'
        }
      }
    }
  }
}