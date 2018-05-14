pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage("Build") {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage("Test") {
            steps {
                parallel (
                    "Maven" : {
                        sh 'mvn test'
                    },
                    "Firefox" : {
                        sh 'echo testing Firefox'
                        sh 'echo more steps'
                    },
                    "Chrome" : {
                        sh 'echo testing Chrome'
                        sh 'echo more steps'
                    }
                )
            }
        }
    }    
}
