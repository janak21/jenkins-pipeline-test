/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'node:16.17.1-alpine' } }
    stages {
        stage('pull') {
            steps {
                sh 'git clone https://github.com/janak21/jenkins-pipeline-test.git && cd jenkins-pipeline-test'
            }
        }stage('build'){
            steps {
                sh 'docker build -t node-app .'
            }
        }stage('deploy'){
            steps {
                sh 'docker run -d weather-app -p 80:8080 localhost/node-app'
            }
        }
    }post {
        success{
            echo 'Your deployment is successful. Please check your application on port 80.'
        }
        failure {
            echo 'Something went wrong. Plese check latest build logs.'
        }
    }
}


