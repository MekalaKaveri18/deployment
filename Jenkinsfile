pipeline{
    agent any
    stages
    {
        stage('Build Docker Image'){
            steps{
                echo "Build docker image"
                bat "docker build -t kubdemoapp:latest"
            }
        }
        stage("Docker Login"){
            steps{
                bat 'docker login -u shivaji108 -p Kaveri@1729 '
            }
        }
        stage('push Docker Image to Docker Hub'){
            steps{
                echo "push Docker Image to Docker Hub"
                bat "docker tag kubdemoapp:latest shivaji108/sample:latest"

                bat "docker push shivaji108/sample:kubeimage1"
            }
        }
        stage('Deploy to kubernetes'){
            //apply deployment and service
            bat 'kubectl apply -f deployment.yaml --validate=false'
            bat 'kubectl apply -f service.yaml'
        }


    }
}
