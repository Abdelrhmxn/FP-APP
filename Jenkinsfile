pipeline {
    agent any

    stages {
        stage('Authentication'){
            steps{
                sh '''
                gcloud auth configure-docker us-central1-docker.pkg.dev
                gcloud container clusters get-credentials abdelrhmxn-gke-cluster --zone us-central1-a --project abdelrhmxn-gcp-project
                '''
            }
        }
        stage('Image Build'){
            steps{
                sh "docker build -t us-central1-docker.pkg.dev/abdelrhmxn-gcp-project/my-repository/hello:${BUILD_NUMBER} ."
            }
        }
        stage('Image Push'){
            steps{
                sh "docker push us-central1-docker.pkg.dev/abdelrhmxn-gcp-project/my-repository/hello:${BUILD_NUMBER}"
            }
        }
        stage('Deploy'){
            steps{
             sh '''
                mv Deployment.yml Deployment.yml.tmp
                cat Deployment.yml.tmp | envsubst > Deployment.yml
                rm -f Deployment.yml.tmp
                kubectl apply -f Deployment.yml
                '''
            }
        }
    }
}
