
pipeline {
    agent any

    stages {
        stage('node build') {
            agent{
                docker{
                    // downloads node alpine image if not exists
                    image "node:18-alpine"
                    // using single workspace instead of one for each stage
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la

                    printf "\\n\\n\\n"
                    #checking node and npm version

                    node --version
                    npm --version

                    printf "\\n\\n\\n"
                    
                    #The npm ci command is used to install dependencies in a Node.js project, 
                    #specifically in CI/CD environments like Jenkins.
                    # It’s faster and more predictable than npm install.

                    npm ci
                    npm run build

                    printf "\\n\\n\\n"

                    echo "After npm build"
                    ls -la
                '''
            }
        }
        stage("Test") {
            agent{
                docker{
                    // we need docker agent to perform npm test 
                    image "node:18-alpine"
                    // using single workspace instead of one for each stage
                    reuseNode true
                }
            }

            steps{
                
                sh '''
                # shell command that checks whether the file build/index.html exists in the current workspace.
                test -f build/index.html
                npm test
                
                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
