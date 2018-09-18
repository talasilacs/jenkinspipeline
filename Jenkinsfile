pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                def shell(command) {
                    return bat(returnStdout: true, script: "sh -x -c \"mvn clean package\"").trim()
                }
            
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
