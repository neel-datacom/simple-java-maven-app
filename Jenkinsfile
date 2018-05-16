pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Test') {
      parallel {
        stage('Maven') {
          steps {
            sh 'mvn test'
          }
        }
        stage('Firefox') {
          steps {
            sh 'echo testing Firefox'
            sh 'echo more steps'
          }
        }
        stage('Chrome') {
          steps {
            sh 'echo testing Chrome'
            sh 'echo more steps'
          }
        }
      }
    }
    stage('Deploy') {
      parallel {
        stage('Deploy') {
          when {
            expression {
              currentBuild.result == null || currentBuild.result == 'SUCCESS'
            }

          }
          steps {
            sh 'echo Deploy success'
            sh 'echo test'
          }
        }
        stage('test d') {
          steps {
            sh 'echo "d2"'
          }
        }
      }
    }
  }
}