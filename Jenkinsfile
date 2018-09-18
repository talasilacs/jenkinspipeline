pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            
            }
                        post {
                success {
                    echo 'Now Archiving Artifacts...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }

        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying on Linux PreProduction....'
                build job: '2-PipelineAsCode-Dev'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying in Windows Production....'
            }
        }
    }
}
