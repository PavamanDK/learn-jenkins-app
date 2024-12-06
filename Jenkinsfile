pipeline {
    agent any

    stages {
        stage('Parallel Tests') {
            parallel {
                stage('Build') {
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
                }

                stage('Test') {
                    steps {
                        sh '''
                            echo "Executing Test"
                            test -f build/index.html
                            npm test
                        '''
                    }
                }
            }
        }
    }
}