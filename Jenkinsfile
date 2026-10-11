pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking project workspace'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                sh 'mkdir -p build'
                sh 'echo "Jenkins pipeline build successful" > build/app.txt'
                sh 'cat build/app.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'test -s build/app.txt'
                sh 'grep -q "successful" build/app.txt'
                echo 'Tests passed'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p deployed'
                sh 'cp build/app.txt deployed/app.txt'
                sh 'test -s deployed/app.txt'
                echo 'Deployment copy verified'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
