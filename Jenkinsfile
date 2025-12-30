
pipeline {
    agent any

    environment {
        scannerHome = tool "sonar"
    }

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
               sh ' docker build -t borrowimage .'
         }
       }
       stage('image scan') {
          steps {
              sh 'trivy image borrowimage'
         }
      } 
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag borrowimage gopibrahmaiah/library:borrowimage'
                     sh 'docker push gopibrahmaiah/library:borrowimage'
                  }
             }
          }
        }
      }
    }
