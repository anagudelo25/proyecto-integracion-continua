pipeline {
    agent any
    stages {
        stage('Test') {
            when { 
                changeRequest() 
            }
            steps {
                echo "Current Pull Request ID: ${pullRequest.id}"
            }
        }
    }
}