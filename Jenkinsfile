def label = "slave-${UUID.randomUUID().toString()}"
podTemplate(label: label, containers: [
  containerTemplate(name: 'maven', image: 'maven:3.6-alpine', command: 'cat', ttyEnabled: true),
  containerTemplate(name: 'docker', image: 'docker:stable', command: 'cat', ttyEnabled: true),
  containerTemplate(name: 'helm', image: 'alpine/helm:latest', command: 'cat', ttyEnabled: true),
  containerTemplate(name: 'kubectl', image: 'cnych/kubectl', command: 'cat', ttyEnabled: true)
], volumes: [
  hostPathVolume(mountPath: '/root/.m2', hostPath: '/var/run/m2'),
  hostPathVolume(mountPath: '/home/jenkins/.kube', hostPath: '/root/.kube'),
  hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock')
]) {
node(label) {
    stage('copy code'){
        checkout scm
        container('docker'){
            sh """
                docker info
            """
        }
    }
    stage('run helm'){
        container('helm') {
            sh """
                helm version --kubeconfig /home/jenkins/.kube/conf
            """
        }
    }
    stage('mvn test'){
        container('maven'){
            echo "mvn"
        }
    }
    stage ('run kubectl'){
        container('kubectl'){
            sh """
                kubectl get pods --kubeconfig /home/jenkins/.kube/conf
            """
        }
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
}
