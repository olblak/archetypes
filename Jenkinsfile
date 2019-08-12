pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '20'))
    }
    agent {
        label 'docker'
    }
    stages {
        stage('main') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    sh '''
                        docker version
                        docker system prune --all --force
                        DOCKER_BUILDKIT=1 docker build --progress plain --no-cache .
                    '''
                }
            }
        }
    }
}
