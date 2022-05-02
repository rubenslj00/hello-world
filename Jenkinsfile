pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh "mvn -f pom.xml clean install"
            }
        }
        stage('Move war file to docker') {
            steps {
                sh "cp webapp/target/*.war ."
            }
        }
        stage('Build, tag and push image to docker hub') {
            steps {
                sh "echo building image"
                sh "docker build -t web_application ."
            }
        }
    }
}
