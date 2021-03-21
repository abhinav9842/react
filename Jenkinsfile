properties([
    pipelineTriggers([githubPush()]), buildDiscarder(logRotator(numToKeepStr: '3'))
])

node {
    

    stage('checkout scm') {
        echo "hellot123"
        if(env.BRANCH_NAME == 'main'){
        echo 'checking out repo'
        git branch: 'main', credentialsId: 'git-id', url: 'https://github.com/abhinav9842/react'
        echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
        sh "echo ${env.BRANCH_NAME}"
        }
       
    }
    stage('build dev'){
         if(env.BRANCH_NAME == 'main'){
        sh 'docker build -t node-dev -f Dockerfile.dev .' 
     }
      }
    stage('node test'){
        if(env.BRANCH_NAME == 'main'){
       sh 'docker run -e CI=true node-dev npm test'
    }}
    stage('clean up workspace'){
        cleanWs()
        if(env.BRANCH_NAME == 'main'){
             sh 'docker image rm -f node-dev'}
    }
}
