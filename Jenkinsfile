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

            [
                'plik1.txt',
                'plik2.txt',
                'plik3.txt',
            ].each { zmienna ->
                sh """
                    echo aqq > ${zmienna}
                """
            }

            wynik = sh(script: '''
                echo 456
            ''', returnStdout: true)

            echo "wynik: ${wynik}"

            archiveArtifacts '**/artefakt.txt'
            archiveArtifacts 'plik*.txt'
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
