pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'NodeJS' 
        PATH = "$NODEJS_HOME/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your repository
                git 'https://github.com/azizswebni/todo-devops.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'scp -r build/* user@your-server:/path/to/deploy' 
            }
        }
    }

    post {
        success {
            echo 'React app successfully built and deployed!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
