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
        // stage('Sonar Scan'){
        //     steps{
        //         sh 'ls -ltr'
        //         sh "sonar-scanner"
        //     }
        // }
        stage('Build'){
            steps{
                sh 'ls -ltr'
                sh 'zip -r ./* --exclude=.git'
            }
        }
        stage('Deploy'){
            steps{
                echo "Deployment"
            }
        }
        
    }
        post{
            always{
                echo 'cleaning up workspaced'
                //deleteDir()
            }
        }
}