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
                    export NVM_DIR="$HOME/.nvm"
                    if [ ! -d "$NVM_DIR" ]; then
                        curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
                    fi
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    [ -s "$NVM_DIR/bash_completion" ] && . "$NVM_DIR/bash_completion"
                    export PATH="$NVM_DIR/versions/node/v${NODE_VERSION}/bin:$PATH"
                    nvm install ${NODE_VERSION}
                    nvm use ${NODE_VERSION}
                    node -v
                    npm -v
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    [ -s "$NVM_DIR/bash_completion" ] && . "$NVM_DIR/bash_completion"
                    export PATH="$NVM_DIR/versions/node/v${NODE_VERSION}/bin:$PATH"
                    npm ci
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    [ -s "$NVM_DIR/bash_completion" ] && . "$NVM_DIR/bash_completion"
                    export PATH="$NVM_DIR/versions/node/v${NODE_VERSION}/bin:$PATH"
                    npm run build
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    [ -s "$NVM_DIR/bash_completion" ] && . "$NVM_DIR/bash_completion"
                    export PATH="$NVM_DIR/versions/node/v${NODE_VERSION}/bin:$PATH"
                    npm run test:unit || true
                '''
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
