pipeline {
    agent any

    stages {
        stage('pull source code') {
            steps {
                sh "git clone https://github.com/tpouche94/hello-world.git"
            }
        }
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
