pipeline {
    agent any
    environment {
        CI = 'true' 
    }
    stages {
        stage('Git Clone') {
            //Clones Application from GitHub
            steps {
                git 'https://github.com/marbellacovino/simple-node-js-react-npm-app.git'
            }
        }
        stage('Build project with NPM') {
            //Installs Project  Dependencies into the node_modules/ directory
            steps {
                echo 'sh: npm install'
            }
        }
        stage('Test app renders without crashing') { 
            //Runs all tests
            //Unit Tests with the Jest tool and Integration Tests with Enzyme
            steps {
                echo 'sh "npm run test"'
            }
        }
        stage('Build React App') { 
            //Build and Deploy the Application
            steps {
                echo 'sh: npm run build'
            }
        }
        stage('Build Docker Image') { 
            //Builds Docker Application Image
            steps {
                echo 'bat "docker build -t marbellacovino/react-app:v.1.0 ."'
            }
        }
        stage('Docker Publish') {
            //Publishes the Build Image at Docker Registry
            steps {
               echo 'Publishing....'
               echo 'bat "docker push marbellacovino/react-app:v.1.0"'
            }
        }
        stage('Deploy to Kubernetes'){
            //Deploys App in K8s
            steps{
              echo 'bat " kubectl apply -f react-app.yaml"'
              echo 'bat " kubectl apply -f service.yaml"'
            }
        }
    }
}