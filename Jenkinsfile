DEFAULT_BRANCH = 'master default branch'

pipeline {
    agent any
    // agent { 
    //     docker { 
    //         image 'python:3.5.1' 
    //     } 
    // }
    options {
        timestamps()
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
    }

    parameters {
        string(defaultValue: 'master', description: 'branch', name: 'GIT_BRANCH')
    }

    post {
        always {
            echo "Always"
        }
        failure {
            echo "Failure"
        }
        success {
            echo "Success"
        }
    }
    stages {
        stage('first stage') {
            when {
                expression { env.GIT_BRANCH == 'master'}
            }
            steps {
                script {
                    print this.declaredFields
           .findAll { !it.synthetic }
           .each { println "${Modifier.toString( it.modifiers )} ${it.name} : ${it.type}" }
                }
                echo "------------------------"
                echo params.GIT_BRANCH
                echo env.GIT_BRANCH
                echo DEFAULT_BRANCH
                echo "------------------------"
                sh 'python --version'
                sh 'ls'
                sh 'pwd'
                // error('고의적인 에러')
            }
        }
        stage('second stage') {
            post {
                 always {
                    echo "Seconds Stage"
                }
            }
            steps {
                echo env.GIT_BRANCH
                sh 'python --version'
                script {
                    def browsers = ['chrome', 'firefox']
                    for (int i = 0; i < browsers.size(); ++i) {
                        echo "Testing the ${browsers[i]} browser"
                    }
                }
            }
        }
    }
}