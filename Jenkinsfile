
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
               sh ' docker build -t authimage .'
         }
       }
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag authimage gopibrahmaiah/library:authimage'
                     sh 'docker push gopibrahmaiah/library:authimage'
                  }
             }
          }
        }
      }
    }
