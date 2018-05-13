pipeline {
    agent any
    
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }
    
    stages {
        stage('Build') {
            steps {
                bat 'set'
                retry(3) {
                    bat 'echo "Hello world"'
                }
                timeout(time: 3, unit: 'MINUTES') {
                    bat 'dir'
                }
            }
            post {
                always {
                    echo 'This will always run'
                    deleteDir() /*clean up our workplace*/
                }
                success {
                    echo 'successed..'
                    echo 'failure..'
                    mail to: 'kelvin.mai@oocl.com',
                         subject: "Successed Pipeline: ${currentBuild.fullDisplayName}",
                         body: "Something is wrong with ${env.BUILD_URL}"
                }
                failure {
                    echo 'failure..'
                    mail to: 'kelvin.mai@oocl.com',
                         subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                         body: "Something is wrong with ${env.BUILD_URL}"
                }
            }
        }
    }
}
 
