pipeline {
    agent any
    options {
        skipDefaultCheckout true
    }
    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
        stage('Deploy') {
            steps {
                sh './deploy.sh'
            }
        }
    }
    post {
        always {
            githubStatus context: 'continuous-integration/jenkins', state: 'success'
            if (env) {
                githubComment message: "The pipeline completed successfully!"
                githubLabel labels: ['approved']
            }
        }
    }
}