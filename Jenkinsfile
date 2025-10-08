pipeline{ 
    agent any
    stages{
        stage('Build Docker Image'){
            steps{
                echo "Build Docker Image"
                bat "docker build -t kubedemoapp:v1 ."
            }
        }
        stage('Docker Login'){
            steps{
                bat 'docker login -u shivaji108 -p Kaveri@1729'
            }
        }
        stage('push Docker image to docker hub'){
            steps{
                echo "push Docker image to docker hub"
                bat 'docker tag kubedemoapp:v1 shivaji108/sample:kuberimg1'
                bat 'docker push shivaji108/sample:kuberimg1'
            }
        }
        stage('Deploy to Kubernetes'){
            steps{
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
}
