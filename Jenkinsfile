pipeline {
    agent any
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
            steps {
                timeout(time: 15, unit: 'SECONDS') {
                    sh '''
                        ./run-tests
                        sleep 10
                    '''
                }
                sh '''
                    echo test hook 3
                '''
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
