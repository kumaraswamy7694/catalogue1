pipeline {
    agent { node { label 'AGENT-1' } }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Unit test'){
            steps{
                echo "unit test is done here."
            }
        }
        
    }
}