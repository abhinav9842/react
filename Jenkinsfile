node {
    

    stage('build') {
        properties([pipelineTriggers([[$class: 'GitHubPushTrigger']])])
        if (env.BRANCH_NAME == 'master') {
            echo 'I only execute on the main branch'
        } else {
            echo 'I execute elsewherem'
        }
    }
}