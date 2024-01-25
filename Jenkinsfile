pipeline {
    agent any
    tools {
        nodejs 'NodeJS' // The name given to the Node.js installation in Jenkins' Global Tool Configuration
    }
    stages {
        stage('Lint') {
            steps {
                // Run htmlhint using npx, which comes with npm
                bat 'npx htmlhint *.html'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Build the Docker image with a tag 'my-app'
                bat 'docker build -t my-app .'
            }
        }
        stage('Test') {
            steps {
                // Check if index.html contains the expected text
                bat 'findstr "Hello World, my name is Oluwatosin Jegede" index.html'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy using kubectl to apply the deployment configuration
                bat 'kubectl apply -f deployment.yaml'
            }
        }
    }
}