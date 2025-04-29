
pipeline {
    agent any

    stages {
        stage('node build') {
            agent{
                docker{
                    image "node:18-alpine"
                    reuseNode true
                }
            }
            steps {
                sh '''
                ls -la

                echo ""
                echo ""
                echo ""
                node --version
                npm --version
                echo ""
                echo ""
                echo ""
                npm ci
                npm run build
                echo ""
                echo ""
                echo ""
                echo "After npm build"
                ls -la
                '''
            }
        }
    }
}
