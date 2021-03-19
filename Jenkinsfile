properties([pipelineTriggers([githubPush()])])

node {
    

    stage('checkout scm') {
        echo 'checking out repo'
        git branch: 'main', credentialsId: 'git-id', url: 'https://github.com/abhinav9842/react'

    }
}
