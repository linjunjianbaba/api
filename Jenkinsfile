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
            echo 'This is master'
        }
    }
}
