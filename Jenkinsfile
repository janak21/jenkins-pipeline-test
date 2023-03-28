/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    stages {
        stage('pull') {
            steps {
                sh 'rm -rf *'
                sh 'git clone https://github.com/janak21/jenkins-pipeline-test.git && cd jenkins-pipeline-test'
                sh 'ls -la'
            }
        }
        stage('build'){
            steps {
                sh 'docker build -t node-app jenkins-pipeline-test'
            }
        }
        stage('deploy'){
            steps {
                sh 'docker run -d -p 80:8080 localhost/node-app'
            }
        }
    }
    post {
        success{
            echo 'Your deployment is successful. Please check your application on port 80.'
        }
        failure {
            echo 'Something went wrong. Please check latest build logs.'
        }
    }
}
