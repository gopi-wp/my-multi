
pipeline {
    agent any


    stages {

        stage('cleanws') {
            steps {
                cleanWs()
            }
        }
    }

        stage('Code') {
            steps {
                git 'https://github.com/gopi-wp/python-code-library-app.git'
            }
        }

        stage('image build') {
            steps {
               sh ' docker build -t bookimage .'
         }
       }
       stage('image scan') {
          steps {
              sh 'trivy image bookimage'
         }
      } 
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag bookimage gopibrahmaiah/library:bookimage'
                     sh 'docker push gopibrahmaiah/library:bookimage'
                  }
             }
          }
        }
      }
