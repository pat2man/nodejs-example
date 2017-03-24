#!groovy

pipeline {
    agent { label 'nodejs' }

    stages {
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Trigger Build') {
            when {
                branch 'master'
            }

            steps {
                openshiftBuild(bldCfg: 'nodejs-example', namespace: 'jenkins-test')
            }
        }
    }
}