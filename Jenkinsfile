pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh "docker build -t mynodeapp ."
            }
        }
        /*stage("Run") {
            steps {
                sh "docker run -p 3000:3000 mynodeapp"
            }
        }*/
        stage("Deploy") {
            steps {
              def app = 'mynodeapp'
              def dockerapp = 'my-app'
              def version = env.BUILD_NUMBER
              def dockerRegistry = 'docker.io'
              def dockerUser = 'masnawirahmat'
              //def dockerPass = credentials('your-docker-hub-credentials-id')
              //def dockerImage = "${dockerUser}/${app}:${version}"
                withCredentials([usernamePassword(credentialsId: 'mydockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                  sh "echo $PASSWORD | docker login --username $USERNAME --password-stdin ${dockerRegistry}"
                  sh "docker tag ${app} ${dockerUser}/${dockerapp}:${version}"
                  //sh "docker tag ${dockerImage} ${dockerRegistry}/${dockerRepo}:${dockerImage}-${dockerImageTag}"
                  sh "docker push ${dockerUser}/${dockerapp}:${version}"
                  //sh "docker push ${dockerRegistry}/${dockerRepo}:${dockerImage}-${dockerImageTag}"               
                  sh "docker logout"
                }
            }
        }
    }
}
