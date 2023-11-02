pipeline {
    agent any

    stages {
        stage('Image Build'){
            steps{
                sh 'docker build -t us-central1-docker.pkg.dev/abdelrhmxn-gcp-project/my-repository/hello .'
            }
        }
        stage('Image Push'){
            steps{
                sh 'docker push us-central1-docker.pkg.dev/abdelrhmxn-gcp-project/my-repository/hello'
            }
        }
        stage('Deploy'){
            steps{
                sh 'kubectl apply -f Deployment.yml'
            }
        }
    }
}
