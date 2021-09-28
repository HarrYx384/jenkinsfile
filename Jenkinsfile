pipeline{
    agent any
    stages{
        stage("Source code checkout"){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/HarrYx384/binmile.git']]])
                
            }
        }
         stage("docker login"){
            steps{
                withCredentials([string(credentialsId: 'harry', variable: 'dockerhub')]) {
                sh 'docker login -u harry7985 -p ${dockerhub}'
}
            }
        }
        stage("build dockerfile"){
            steps{
                sh 'docker image build -t $JOB_NAME:V1.$BUILD_ID .'
                sh 'docker image tag $JOB_NAME:V1.$BUILD_ID harry7985/$JOB_NAME:V1.$BUILD_ID'
                sh 'docker image tag $JOB_NAME:V1.$BUILD_ID harry7985/$JOB_NAME:latest'
                sh 'docker image push harry7985/$JOB_NAME:V1.$BUILD_ID'
                sh 'docker image push harry7985/$JOB_NAME:latest'
                sh 'docker image rmi -f $JOB_NAME:V1.$BUILD_ID harry7985/$JOB_NAME:V1.$BUILD_ID harry7985/$JOB_NAME:latest'

            }
        }
    }
    
}
