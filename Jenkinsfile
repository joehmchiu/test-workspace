pipeline {
  environment {
    bakdir = '~/backup/test-workspace'
  }

  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Hi, GeekFlare. Starting to build the App.'
      }
    }
    stage('Test') {
      steps {
        echo "testing..."
        sh "ls -lRrth"
      }
    }
    stage('Workspace Check') {
      steps {
        echo "testing..."
        sh "ls -lRthr '${WORKSPACE}'"
      }
    }
    stage('Deploy') {
      parallel {
        stage('Deploy start ') {
          steps {
            echo "Start the deploy .."
            script {
              def props = readJSON file: 'hello.json'
              props.each { key, value ->
                  echo "Walked through key and value: [$key => $value]"
              }
            }
          }
        }
      }
    }
    stage('Prod') {
      steps {
        echo "App is Prod Ready"
      }
    }
    stage('Backup Workspace') {
      steps {
        echo "testing..."
        sh "mkdir -p ${bakdir}"
        sh "cp -rf '${WORKSPACE}' ${bakdir}/."
      }
    }
  }
}
