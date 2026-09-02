pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image node:18-alpine
                    reuseNode true
                }
            }
            steps {
                sh '''
                
                    ls -la   #List all files
                    node --vesrion    #Only for checking purpose not mandatory
                    npm --version  #Only for checking purpose not mandatory 
                    npm ci
                    npm run build
                    ls -la
                '''
                
            }
        }
    }
}
