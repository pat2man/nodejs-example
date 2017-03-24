#!groovy

pipeline {
    agent { label 'nodejs' }

    stages {
        stage('Install') {
            steps {
                echo 'Running npm install'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running npm test'
                sh 'npm test'
            }
        }

        stage('Trigger Build') {
            when {
                branch 'master'
            }

            steps {
                echo 'Triggering build of nodejs-example in jenkins-test'
                openshiftBuild(bldCfg: 'nodejs-example', namespace: 'jenkins-test')
            }
        }
    }
}