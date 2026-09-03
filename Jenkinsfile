pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo Asmita's build is perfect"
                    ls -la   #List all files
                    node --version    #Only for checking purpose not mandatory
                    npm --version  #Only for checking purpose not mandatory 
                    npm ci
                    npm run build
                    ls -la
                '''
                
            }
        }
        stage('Test') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                
                    test -f build/index.html
                    npm test
                '''
                
            }
        }
    }
    post{
        always{
            junit 'test-results/junit.xml'
        }
       
    }
}
