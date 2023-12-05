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
                sh 'mkdir -p /kj_deployments/Gert_main'
                sh 'mkdir -p /kj_deployments/Gert_develop'
            }
        }
        stage('Deploy main') {
           when {
             branch 'main'
            }
           steps {
               // Copy the built files to the subdirectory
               sh "cp -r dist/kood-johvi-cicd/browser/* /kj_deployments/Gert_main"
           }
       }

      
        stage('Deploy develop') {
           when {
             branch 'develop'
            }
           steps {
               // Copy the built files to the subdirectory
               sh "cp -r dist/kood-johvi-cicd/browser/* /kj_deployments/Gert_develop"
           }
       }
      // Create a different subfolder based on your name with branch suffix (ex. /kj_deployments/andreas_main, /kj_deployments/andreas_develop)
// Build and deploy main branch to /kj_deployments/yourname_main
// Builds and deploys develop branch to /kj_deployments/yourname_develop
    }
}
