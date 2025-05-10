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
            steps{
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Test Stage'
                if [ -f build/index.html ]; then
  echo "File exists: build/index.html"
else
  echo "Error: File not found - build/index.html"
fi
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
