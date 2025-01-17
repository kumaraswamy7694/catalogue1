pipeline {
    agent { node { label 'AGENT-1' } }
    stages {
        stage('Get version'){
            steps{
                script{
                    def packageJson = readJSON file: 'package.json'
                    def packageVersion = packageJson.version
                    echo "${packageJSON.version}"
                }
            }
        }
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
        stage('Sonar Scan'){
            steps{
                echo "sonar scan done"
            }
        }
        stage('Build'){
            steps{
                sh 'ls -ltr'
                sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip '
            }
        }
        stage('SAST'){
            steps{
                echo " SAST Done"
            }
        }
    //     // install pipeline utiluty if not installed
    //    stage('Publish Artifact'){
    //         steps{
    //             nexusArtifactUploader(
    //             nexusVersion: 'nexus3',
    //             protocol: 'http',
    //             nexusUrl: '172.31.26.222:8081/',
    //             groupId: 'com.roboshop',
    //             version: '1.0.1',
    //             repository: 'catalogue',
    //             credentialsId: 'nexus-auth',
    //             artifacts: [
    //              [artifactId: 'catalogue',
    //               classifier: '',
    //               file: 'catalogue.zip',
    //               type: 'zip']
    //     ]
    //  )
    //         }
    //     }
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