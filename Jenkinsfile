#!groovy

node ('nodejs') {
    stage('Debug') {
        echo 'Listing path and files'
        sh 'pwd'
        sh 'find ./'
    }

    stage('Install') {
        echo 'Running npm install'
        sh 'npm install'
    }

    stage('Test') {
        echo 'Running npm test'
        sh 'npm test'
    }

    stage('Trigger Build') {            
        echo 'Triggering build of nodejs-example in jenkins-test'
        openshiftBuild(bldCfg: 'nodejs-example', namespace: 'jenkins-test')
    }
}