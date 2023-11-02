pipeline {
    agent any

    stages {
        stage('Image Build'){
            steps{
                docker build -t us-central1-docker.pkg.dev/abdelrhmxn-gcp-project/my-repository/hello . 
            }
        }
        stage('Image Push'){
            steps{
                docker push us-central1-docker.pkg.dev/abdelrhmxn-gcp-project/my-repository/hello
            }
        }
        stage('Deploy'){
            steps{
                kubectl apply -f Deployment.yml
            }
        }
    }
}