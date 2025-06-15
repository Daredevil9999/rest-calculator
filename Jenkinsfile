pipeline {
    agent any

    tools{
        maven "jenkins-maven"
    }

    parameters {
        gitParameter (defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH', branchFilter: '.*', description: 'Select branch to build')
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: "${params.BRANCH}", url: 'https://github.com/Daredevil9999/rest-calculator.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}