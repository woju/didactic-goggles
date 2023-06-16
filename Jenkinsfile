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
                sh '''
                    echo test hook 6
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
            sh 'curl https://xfd.woju.eu/0'
        }
        failure {
            sh 'curl https://xfd.woju.eu/1'
        }
    }
}
