pipeline {
    def shell(command) {
    return bat(returnStdout: true, script: "sh -x -c \"${command}\"").trim()
    }
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
