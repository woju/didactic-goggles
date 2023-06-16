node {
    checkout scm

        stage('Build') {
            sh '''
                # make
                # make install DESTDIR=...
            '''

            if (env.JENKINS_URL == 'http://23.101.54.168/') {
                sh '''
                    echo tak, to ten jenkins (${JENKINS_URL})
                '''
            } else {
                sh """
                    echo to nie ten jenkins: ${env.JENKINS_URL}
                """
            }
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
