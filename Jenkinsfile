
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

                    printf "\\n\\n\\n"

                    node --version
                    npm --version

                    printf "\\n\\n\\n"

                    npm ci
                    npm run build

                    printf "\\n\\n\\n"

                    echo "After npm build"
                    ls -la
                '''
            }
        }
    }
}
