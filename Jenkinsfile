#!groovy

node ('nodejs') {
    stage('Checkout') {
        echo "Checkout out from Git"
        checkout scm
    }

    stage('Install Dependencies') {
        echo 'Running npm install'
        sh 'npm install'
    }

    stage('Test') {
        echo 'Running npm test'
        sh 'npm test'
    }

    stage('Trigger Build') {            
        echo 'Triggering build of nodejs-example in jenkins-test'
        openshiftBuild(bldCfg: 'nodejs-example-app', namespace: 'jenkins-test')
    }
}