
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository to a workspace
                git credentialsId: 'jenkins-cicd', url: 'git@github.com:kunaldenvr/jenkins-pipeline.git',
                branch: 'main'
            }
        }

        stage('Modify Files') {
            steps {
                // Perform any necessary modifications to the files in the workspace
                sh 'echo "Hello, Argocd!" > argocd.txt'
            }
        }

        stage('Commit and Push') {
            steps {
                // Add all modified files to the Git repository
                sh 'git config --global --add safe.directory /var/lib/jenkins/workspace/pipeline'
                sh 'git add .'
                
                // Commit the changes
                sh 'git commit -m "Update files via Jenkins"'
                // sh 'git config --global user.email "kunal@denvrdata.com"'
                // sh 'git config --global user.name "kunal"'
                // sh 'git branch -M main'
                // sh 'git push git@github.com:kunaldenvr/jenkins-pipeline.git HEAD:main'
                // Push the changes back to the GitHub repository
                sh 'git push origin main' // Replace "main" with the branch you want to push to
            }
        }
    }
}