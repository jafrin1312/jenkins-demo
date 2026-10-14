pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code is available from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building my application..."'
                sh 'mkdir -p build'
                sh 'echo "Hello from my GitHub webhook!" > build/app.txt'
                sh 'cat build/app.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'test -f build/app.txt'
                sh 'grep -q "Hello from my GitHub webhook" build/app.txt'
                echo 'All tests passed!'
            }
        }

        stage('Package') {
            steps {
                sh 'tar -czf app.tar.gz build/'
                sh 'ls -lh app.tar.gz'
            }
        }
    }

    post {
        success {
            echo 'CI/CD pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
