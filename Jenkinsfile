pipeline {
    agent any
 
    environment {
        GIT_BRANCH_MASTER = 'master' // Name of the development branch
        GIT_BRANCH_DEVELOPMENT = 'development' // Name of the quality assurance branch
    }
 
    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                checkout scm
            }
        }
        stage('Merge to DEVELOPMENT') {
            steps {
                script {
                    // Merge the development branch into the QA branch
                    sh "git checkout ${GIT_BRANCH_DEVELOPMENT}"
                    sh "git merge origin/${GIT_BRANCH_MASTER}"
                    // Push the changes to the remote QA branch
                    sh "git push origin ${GIT_BRANCH_DEVELOPMENT}"
                }
            }
        }
    }
}
