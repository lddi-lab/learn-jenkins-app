pipeline {
    agent any
    
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true

                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Test stage'
                sh '''
                    (ls /build/index.html >> /dev/null 2>&1 && echo yes) || echo no
                    npm test
                '''
            }

        }
           
    }
}