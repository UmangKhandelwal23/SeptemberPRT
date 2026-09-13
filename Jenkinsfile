pipeline {
    agent { label 'Slave01' }

    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker')
    }

    stages {

        stage('git') {
            steps {
                git branch: 'main', url: 'http://github.com/UmangKhandelwal23/SeptemberPRT'
            }
        }

        stage('docker build') {
            steps {
                sh 'sudo docker build -t umangkhandelwal/septemberprt:v1 .'
            }
        }

        stage('Docker Push') {
            steps {
                sh '''
                echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login -u "$DOCKERHUB_CREDENTIALS_USR" --password-stdin
                docker push umangkhandelwal/septemberprt:v1
                '''
            }
        }

       
    }
}
