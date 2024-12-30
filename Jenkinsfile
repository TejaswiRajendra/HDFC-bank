pipeline {
    agent any

    options {
        skipDefaultCheckout() // Avoids checking out code by default
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the current branch from the GitHub repository
                checkout scm
            }
        }
        stage('Lint HTML') {
            steps {
                echo 'Linting HTML files...'
                // Use an HTML linter like tidy (ensure it's installed on the agent)
                sh 'tidy -errors *.html || true'
            }
        }
        stage('Test HTML') {
            steps {
                echo 'Running tests on HTML files...'
                // Example: Use a custom script or tool for testing
                // Replace this with your specific testing commands
                sh './run-html-tests.sh'
            }
        }
        stage('Deploy') {
            when {
                branch 'main' // Deploy only from the main branch
            }
            steps {
                echo 'Deploying HTML files...'
                // Deploy to a server or hosting service
                sh './deploy-html.sh'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            cleanWs() // Clean workspace after pipeline execution
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
