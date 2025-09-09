pipeline {
    agent any
    tools {
        go '1.19'
    }

    environment {
        GO111MODULE='on'
    }

    stages {
        stage('Test') {
            steps {
                // pull project from github
                git 'https://github.com/AdminTurnedDevOps/go-webapp-sample.git'

                // run all of the tests in project
                sh 'go test ./..'
            }
        }

        stage('Build') {
            git 'https://github.com/AdminTurnedDevOps/go-webapp-sample.git'

            // build project
            sh 'go build .'
        }

        stage('Run') {
            steps {
                // binary file from build gets stored in pipeline directory
                sh 'cd /var/lib/jenkins/workspace/go-full-pipeline && go-webapp-sample &'
            }
        }
    }
}