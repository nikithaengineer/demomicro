pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/nikithaengineer/demomicro.git'
        BRANCH_NAME = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: "${BRANCH_NAME}", url: "${REPO_URL}"
            }
        }

        stage('Build') {
            steps {
                echo 'Running build commands...'

                // Adjust commands based on your project type
                // For Python:
                // sh 'python3 demomicro/app.py'

                // For Node.js:
                // sh 'cd demomicro && npm install && npm start'

                // For Java:
                // sh 'cd demomicro && javac Main.java && java Main'

                // Simple test: list files
                sh 'echo "Listing files in workspace:"'
                sh 'ls -l demomicro || ls -l'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: 'demomicro/**, *.txt', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully! 🎉'
        }
        failure {
            echo 'Build failed. ❌'
        }
    }
}
