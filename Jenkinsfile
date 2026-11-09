pipleline{
    agent any
    stages{
        stage('Build Docker Image'){
            steps{
                echo 'Building Docker Image'          
                bat 'docker build -t kubedemoapp .'
                }
        }
        stage('Docker login'){
            steps{
                echo 'Dcoker login'
                batch 'docker login -u rentalabindupriya -p bindupriya@19'
            }
        }
        stage('Push Docker Image to Docker Hub'){
            steps{
                echo 'Pushing Docker Image to Docker Hub'
                bat 'docker tag kubedemoapp:v1 rentalabindupriya/sample2026:kubeimage1'
                bat 'docker push rentalabindupriya/sample2026:kubeimage1'
            }
        }
        stage('Deploy to kubernetes'){
            steps{
                echo 'Deploying to Kubernetes'
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
    post{
        success{
        echo 'Compiled successfully'
        }
        failure{
        echo 'failed to compile'
        }
    }
}
