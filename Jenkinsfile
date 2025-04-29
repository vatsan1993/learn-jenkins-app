
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



                node --version
                npm --version


                npm ci
                npm run build

                
                echo "After npm build"
                ls -la
                '''
            }
        }
    }
}
