pipeline {
    agent any
    tools{
        nodejs "nodejs21"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: "main", url: 'https://github.com/GitGert/KoodJohviCICD'
            }
        }
        stage('npm install') {
            steps {
                 sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('deploy to server') {
            steps {
                sh 'mkdir -p /kj_deployments/Gert'
            }
        }
        stage('Deploy') {
           steps {
               // Copy the built files to the subdirectory
               sh "cp -r dist/kood-johvi-cicd/browser/* /kj_deployments/Gert"
           }
       }
    }
}
