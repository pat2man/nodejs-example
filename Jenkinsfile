#!groovy

node('nodejs') {
       stage 'Checkout' {
           steps {
               checkout scm
           }
       }

       stage 'Test' {
           steps {
                env.NODE_ENV = "test"
                print "Environment will be : ${env.NODE_ENV}"

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
