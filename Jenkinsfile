pipeline {
    agent any


    stages {

        stage('cleanws') {
            steps {
                cleanWs()
            }
        }

        stage('Code') {
            steps {
                git 'https://github.com/gopi-wp/python-code-library-app.git'
            }
        }
        stage('image build') {
            steps {
               sh ' docker build -t app2 .'
         }
        }
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag app2 gopibrahmaiah/library:app-v2'
                     sh 'docker push gopibrahmaiah/library:app-v2'
                  }
              }
           }
         }
       }
    }
