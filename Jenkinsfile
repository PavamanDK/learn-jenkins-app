pipeline {
    agent any

    stages {
        stage('Parallel Tests') {
           // parallel {
                /*stage('Build') {
                    agent {
                        docker{
                            image 'node:18-alpine'
                            reuseNode true
                        }
                    }
                    steps {
                        sh '''
                            ls -ltrh
                            node --version
                            npm --version
                            npm ci
                            npm run build
                            ls -la
                        '''
                    }
                }*/

                /*stage(' Unit Test') {
                    agent {
                        docker{
                            image 'node:18-alpine'
                            reuseNode true
                        }
                    }
                    steps {
                        sh '''
                            echo "Executing Test"
                            test -f build/index.html
                            npm --version
                            npm test
                        '''
                    }
                }*/

                stage(' E2E Test') {
                    agent {
                        docker{
                            image 'mcr.microsoft.com/playwright:v1.49.0-noble'
                            reuseNode true
                        }
                    }
                    steps {
                        sh '''
                            echo "Executing E2E Test"
                            npm install serve
                            node_modules/.bin/serve -s build &
                            sleep 10
                            npx playwrite test                           
                        '''
                    }
                }
            //}
        }
    }
}