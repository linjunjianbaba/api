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
        if (env.BRANCH_NAME == 'master'){
            echo 'master'
        }
        if (env.BRANCH_NAME == 'test'){
            echo 'test'
        }
        if (env.BRANCH_NAME == 'dev'){
            echo 'dev'
        }
    }
}
