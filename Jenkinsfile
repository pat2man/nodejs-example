#!groovy

pipeline {
    agent { label 'nodejs' }

    stages {
        stage('Test') {
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }

        stage('Build') {
            when {
                branch 'master'
            }

            steps {
                openshiftBuild(bldCfg: 'nodejs-example', namespace: 'jenkins-test')
            }
        }
    }
}