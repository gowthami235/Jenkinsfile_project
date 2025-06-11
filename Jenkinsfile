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
        sh 'mvn compile -Dmaven.compiler.release=11'
      }
    }

    stage('Test Code') {
      steps {
        sh 'mvn test -Dmaven.compiler.release=11'
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
        sh 'mvn package -Dmaven.compiler.release=11'
      }
    }
  }
}
