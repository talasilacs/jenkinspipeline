pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Builing the Maven Project...'
                sh 'mvn clean package'
            }
             post {
                success {
                    echo 'Now Archiving Maven Artifacts...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }

        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying on Linux Staging....'
                build job: '2-PipelineAsCode-Dev'
            }
        }
        stage ('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }

                build job: '3-PipelinAsCode-Prod'
            }
            post {
                success {
                    echo 'Code deployed to Production.'
                }

                failure {
                    echo ' Deployment failed.'
                }
            }
        }
        

    }
}
