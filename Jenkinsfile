pipeline {
    agent {
        dockerfile {
            filename 'Dockerfile'
        }
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
            steps {
                timeout(time: 15, unit: 'SECONDS') {
                    sh '''
                        ./run-tests
                        sleep 10
                    '''
                }
                sh '''
                    curl -s https://example.org/ | grep -F '<title>'
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
        success {
            sh 'curl -s https://xfd.woju.eu/0'
        }
        failure {
            sh 'curl -s https://xfd.woju.eu/1'
        }
    }
}
