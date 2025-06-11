pipeline {
  agent any

  tools {
    // 'mymaven' is the name of Maven configured in Jenkins Tool Configuration
    maven 'mymaven'
  }

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/github-simplilearn-net/MavenBuild.git'
      }
    }

    stage('Compile Code') {
      steps {
        sh 'mvn complie'
      }
    }

    stage('Test Code') {
      steps {
        sh 'mvn test'
      }
      post{
        success{
          // Publish test results to Jenkins dashboard
          junit 'target/surefire-reports/*.xml'
        }
      }
    }

    stage('Package Code') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
