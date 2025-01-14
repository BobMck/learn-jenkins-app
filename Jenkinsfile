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
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
            if [ -e "/var/jenkins_home/workspace/learn-jenkins-app/build/index.html" ]; then
            echo "File exists."
            else
            echo "File does not exist."
            fi
            npm test
            '''
            }
        }
    }
}