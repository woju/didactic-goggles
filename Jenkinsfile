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
                sh '''
                    ./run-tests
                    true
                '''
                sh '''
                    echo poprawka
                '''
            }
        }
    }
}
