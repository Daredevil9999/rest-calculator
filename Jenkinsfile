pipeline {
    agent any

    tools{
       maven "jenkins-maven"
    }

    environment {
        CURRENT_BRANCH = "${env.BRANCH_NAME}"
    }

    stages {
        stage('Info') {
            steps {
                echo "Running on branch: ${env.BRANCH_NAME}"
            }
        }
        stage('Groovy Logic') {
            steps {
                script {
                    def branchesToBuild = ['duplicate-branch', 'master']
                    if (branchesToBuild.contains(env.BRANCH_NAME)) {
                        echo "This is an allowed branch: ${env.BRANCH_NAME}"
                    } else {
                        echo "Skipping branch: ${env.BRANCH_NAME}"
                        currentBuild.result = 'SUCCESS'
                        return
                    }
                }
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
