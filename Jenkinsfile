node {
    checkout scm

        stage('Build') {
            sh '''
                echo 123 > artefakt.txt
            '''

            if (env.JENKINS_URL == 'http://23.101.54.168/') {
                sh '''
                    echo tak, to ten jenkins: ${JENKINS_URL}
                '''
            } else {
                sh """
                    echo to nie ten jenkins: ${env.JENKINS_URL}
                """
            }

            archiveArtifacts '**/artefakt.txt'
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
