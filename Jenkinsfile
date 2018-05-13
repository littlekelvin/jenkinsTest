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
                }
                success {
                    echo 'successed..'
                }
                failure {
                    echo 'failure..'
                }
            }
        }
    }
}
 
