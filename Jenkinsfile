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
               sh ' docker build -t app .'
         }
       }
       stage('image scan') {
          steps {
              sh 'trivy image app'
         }
      } 
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag app gopibrahmaiah/library:app'
                     sh 'docker push gopibrahmaiah/library:app'
                  }
             }
          }
        }
      }
