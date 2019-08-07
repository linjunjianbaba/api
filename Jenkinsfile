pipeline {
    agent any
    stages{
        stage('GitCode'){
            steps{
                checkout scm
            }
        }
        stage('Build'){
            steps{
                echo 'Buinding.....'
            }
        }
        stage('Test'){
            when {
                expression { BRANCH_NAME == 'master' }
            }
            steps{
                echo 'Testing......'
            }           
        }
        stage('Deploy'){
            when {
                expression { BRANCH_NAME == 'master' }
            }
            steps {
                sh 'echo env.BRANCH_NAME'
            }
        }
    }
}
