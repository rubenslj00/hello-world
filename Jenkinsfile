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
                sh "sudo docker build -t web_application ."
                
                sh "echo tagging image"
                sh "sudo docker tag web_application:latest tpouche94/web_application:latest"
                
                sh "echo pushing image to docker hub"
                sh "sudo docker push tpouche94/web_application:latest"
            }
        }
        stage("Deploy application to kubernetes cluster") {
            steps {
                sh "kubectl apply -f yaml-files"
            }
        }
        stage("echo Update deployment with new pods if image is updated in dockerhub") {
            steps {
                sh "kubectl rollout restart deployment.apps/web-regapp"
            }
        }
    }
}
