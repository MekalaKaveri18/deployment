pipeline{
    agent any
    stages
    {
        stage('Build Docker Image'){
            steps{
                echo "Build docker image"
                bat "docker build -t kubdemoapp:v1"
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
                bat "docker tag kubdemoapp:v1 shivaji108/sample:kubeimage"

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
