pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Deploy HTML') {
            steps {
                echo 'Deploying HTML files...'
                sh './load-html.sh'
            }
        }
    }
}
