pipeline {
    agent any
    options {
        timeout(time: 5, unit: 'SECONDS')
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    # make
                    # make install DESTDIR=...
                '''
            }
        }
        stage('Test') {
            timeout(time: 15, unit: 'SECONDS') {
                steps {
                    sh '''
                        ./run-tests
                        sleep 10
                    '''
                }
            }
        }
    }
    post {
        always {
            sh '''
                echo ZAWSZE
            '''
        }
    }
}
