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
    }
}
