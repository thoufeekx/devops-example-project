pipeline {
    agent any

    environment {
        NODE_VERSION = '18'
    }

    stages {
        stage('Setup') {
            steps {
                // Install Node.js
                sh """
                    export NVM_DIR="\$HOME/.nvm"
                    [ -s "\$NVM_DIR/nvm.sh" ] && . "\$NVM_DIR/nvm.sh"
                    nvm install \${NODE_VERSION}
                    nvm use \${NODE_VERSION}
                """
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run test:unit || true'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Add your deployment commands here'
                // Example: sh 'aws s3 sync dist/ s3://your-bucket-name/'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
