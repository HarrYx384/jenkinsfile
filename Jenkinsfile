pipeline{
    agent any
    stages{
        stage("Source code checkout"){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/HarrYx384/binmile.git']]])
                
            }
        }
    }
    
}
