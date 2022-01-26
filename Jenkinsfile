pipeline {
    agent {
        kubernetes {
            defaultContainer 'maven'
            yamlFile 'jdk8-pod.yml'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'id'
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {

                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
