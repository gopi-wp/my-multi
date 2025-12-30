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
               sh ' docker build -t dbimage .'
         }
       }
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag dbimage gopibrahmaiah/library:dbimage-v1'
                     sh 'docker push gopibrahmaiah/library:dbimage-v1'
                  }
             }
          }
        }
      }
   }
