properties([
    pipelineTriggers([githubPush()]), buildDiscarder(logRotator(numToKeepStr: '3'))
])

node {
    

    stage('checkout scm') {
        echo 'checking out repo'
        git branch: 'main', credentialsId: 'git-id', url: 'https://github.com/abhinav9842/react'
        echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
        echo sh(returnStdout: true, script: 'env')
    }
    stage('build dev'){
        sh 'docker build -t node-dev -f Dockerfile.dev .' 
    }
    stage('node test'){
       sh 'docker run -e CI=true node-dev npm test'
    }
    stage('clean up workspace'){
        cleanWs()
        sh 'docker image rm -f node-dev'
    }
}
