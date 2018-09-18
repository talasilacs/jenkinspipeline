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
                build job: '2-PipelibeAsCode-Dev'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
