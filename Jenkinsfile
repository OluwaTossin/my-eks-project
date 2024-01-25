pipeline {
    agent any
    stages {
        stage('Lint') {
            steps {
                // Install htmlhint
                sh 'npm install -g htmlhint'
                // Run htmlhint on all html files
                sh 'htmlhint *.html'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Build the Docker image with a tag 'my-app'
                sh 'docker build -t my-app .'
            }
        }
        stage('Test') {
            steps {
                // Check if index.html contains the expected text
                sh 'grep "Hello World, my name is Oluwatosin Jegede" index.html'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy using kubectl to apply the deployment configuration
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
