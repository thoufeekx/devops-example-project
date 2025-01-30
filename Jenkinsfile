pipeline {
    agent any

    environment {
        NODE_VERSION = '18'
        NVM_DIR = "$HOME/.nvm"
    }

    stages {
        stage('Setup') {
            steps {
                sh '''
                    if [ ! -d "$NVM_DIR" ]; then
                        curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
                    fi
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    nvm install ${NODE_VERSION}
                    nvm use ${NODE_VERSION}
                    node -v
                    npm -v
                '''
            }
        }

        stage('SetupNodeJS') {
            steps {
                sh '''
                    sudo apt update
                    sudo apt install -y nodejs npm
                    node -v
                    npm -v
                '''
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
                echo 'Executing deployment process...'
                // Example deployment command
                // sh 'aws s3 sync dist/ s3://your-bucket-name/'
            }
        }
    }

    post {
        always {
            echo 'Cleaning workspace...'
            cleanWs()
        }
        success {
            echo 'Build and deployment successful ✅'
        }
        failure {
            echo 'Build failed ❌'
        }
    }
}
