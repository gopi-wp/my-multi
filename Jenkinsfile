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
               sh ' docker build -t app1 .'
         }
        }
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag app1 gopibrahmaiah/library:app-v1'
                     sh 'docker push gopibrahmaiah/library:app-v1'
                  }
              }
           }
         }
       }
    }
