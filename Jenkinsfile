/*File: Jenkinsfile*/
pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh "docker build -t mynodeapp ."
            }
        }
        stage("Run") {
            steps {
                sh "docker run -p 3000:3000 mynodeapp"
            }
        }
    }
}
