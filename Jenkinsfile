pipeline {
    agent {
        kubernetes {
            yamlFile 'jdk8-pod.yml'
        }
    }
    stages {
        stage('Build') {
            steps {
                container('maven') {
                    sh 'id'
                    sh 'mvn -B -DskipTests clean package'
                }
            }
        }
        stage('Test') {
            steps {
                container('maven') {
                    sh 'mvn test' 
                }
                post {
                    always {
                        container('maven') {
                            junit 'target/surefire-reports/*.xml' 
                        }
                    }
                }
            }
        }
    }
}
