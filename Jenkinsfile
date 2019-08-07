node {
    stage('GitCode'){
        checkout scm
    }
    stage('Build'){
        echo 'Buinding.....'
    }
    stage('Test'){
        echo 'Testing......'
    }
    stage('Deploy'){
        when {
            expression { BRANCH_NAME ==~ /release\/.*/ }
        }
        steps {
           sh './gradlew firTest'
        }
    }
}
