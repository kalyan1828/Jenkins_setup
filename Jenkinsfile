pipeline {
    agent any

    stages {
        stage('Code') {
            steps {
                git 'https://github.com/kalyan1828/nginix_dockerfile.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage('Deploy') {
            steps {
               sh 'docker run -itd --name container1 -v /usr/share/nginx/html --network hello -p 1234:80 image1' 
            }
        }
        stage('destroyConatiner') {
            input{
                message "destroy container yes/no"
            }
            steps {
               sh 'docker kill container1'
               sh 'docker rm container1'
            }
        }
    }
}
