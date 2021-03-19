properties([
    pipelineTriggers([githubPush()]), buildDiscarder(logRotator(numToKeepStr: '3'))
])

node {
    

    stage('checkout scm') {
        echo 'checking out repo'
        git branch: 'main', credentialsId: 'git-id', url: 'https://github.com/abhinav9842/react'

    }
    stage('build dev'){
        sh 'docker build -t node-dev -f Dockerfile.dev .' 
    }
    stage('node test'){
       sh 'docker run node-dev npm run test'
    }
    stage('clean up workspace'){
        cleanWs()
    }
}
