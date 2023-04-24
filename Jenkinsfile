pipeline {
    agent {
        docker {
            image 'node:lts-bullseye-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }

        stage('Test') { 
            steps {
                sh 'npm test' 
            }
        }

        stage('Deploy') { 
            steps {
                sh 'npm run build' 
                sh 'docker build -t my-react-app .' 
                sh 'docker run -d -p 3000:3000 my-react-app' 
            }
        }
    }
}