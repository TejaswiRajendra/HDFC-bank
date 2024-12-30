pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from your repository
                checkout scm
            }
        }
        stage('Lint HTML') {
            steps {
                echo 'Linting HTML files...'
                // Using htmlhint for linting (ensure Node.js and htmlhint are installed)
                sh '''
                if ! command -v htmlhint &> /dev/null; then
                    echo "htmlhint not found. Installing..."
                    npm install -g htmlhint
                fi
                htmlhint *.html || echo "Linting completed with warnings/errors."
                '''
            }
        }
        stage('Test HTML') {
            steps {
                echo 'Testing HTML files...'
                // Replace with actual HTML testing commands or scripts
                sh './test-html.sh'
            }
        }
        stage('Package or Deploy') {
            steps {
                echo 'Packaging or Deploying HTML files...'
                // Example deployment to a web server
                sh './deploy-html.sh'
            }
        }
    }

    post {
        always {
            echo 'Cleaning workspace...'
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}

  
