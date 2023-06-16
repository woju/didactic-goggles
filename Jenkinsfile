node {
	checkout scm

        stage('Build') {
                sh '''
                    # make
                    # make install DESTDIR=...
                '''
        }
        stage('Test') {
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
