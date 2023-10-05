pipeline {
    agent any
    stages{
        stage("Build Docker images") {
           steps{
                sh '''
                    echo "Building images"
                    docker build -t nareshm5859/duo-nm-flask:latest .
                    docker push nareshm5859/duo-nm-flask
                '''
           }
        }
        stage("Deploy containers to k8s") {
           steps{
                sh '''
                kubectl rollout restart deployment --namespace=nm-jenkins-dev flask-app
                '''
           }
        }
    }
}