pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                echo "Checking version & build" 
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                echo "done with the build"
                  '''
            }
        }
    }
    post {
        always {
            sh '''
            echo 'zipping the artifact'
            echo 'uploading the artifact'
            '''
        }
    }
}

