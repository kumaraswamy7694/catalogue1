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
                sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip '
            }
        }

       stage('Publish Artifact'){
            steps{
                nexusArtifactUploader(
                nexusVersion: 'nexus3',
                protocol: 'http',
                nexusUrl: '18.234.223.39:8081/',
                groupId: 'com.roboshop',
                version: '1.0.1',
                repository: 'catalogue',
                credentialsId: 'nexus-auth',
                artifacts: [
                 [artifactId: 'catalogue',
                  classifier: '',
                  file: 'catalogue.zip',
                  type: 'zip']
        ]
     )
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