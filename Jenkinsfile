pipeline {
    environment {
        CI = 'true' 
    }
    stages {
        stage('Git Clone') {
            steps {
                git 'https://github.com/marbellacovino/simple-node-js-react-npm-app.git'
            }
        }
        stage('Build project with NPM') {
            steps {
                echo 'sh: npm install'
            }
        }
        stage('Test app renders without crashing') { 
            steps {
                echo 'sh: "npm install --save-dev cross-env'
                echo 'sh "npm run test"'
            }
        }
        stage('Build and Release') { 
            steps {
                echo 'sh: npm run build nodejs-react-app --prod'
            }
        }
        stage('Build Docker Image') { 
            steps {
                echo 'bat "docker build . -t react-app:v.1.0"'
            }
        }
        stage('Docker Publish') {
            steps {
               echo 'Publishing....'
               echo 'bat "docker push react-app:v.1.0"'
            }
        }
        stage('Deploy to Kubernetes'){
            steps{
              echo 'Deployinging....'
              echo 'bat " kubectl delete -f react-app.yaml"'
              echo 'bat " kubectl apply -f react-app.yaml"'
            }
        }
    }
}