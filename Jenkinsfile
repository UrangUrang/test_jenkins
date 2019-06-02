
DEFAULT_BRANCH = 'master'

pipeline {
    agent { docker { image 'python:3.5.1' } }
    options {
        timestamps()
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
    }

    parameters {
        string(defaultValue: 'master', description: 'branch', name: 'GIT_BRANCH')
    }

    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
