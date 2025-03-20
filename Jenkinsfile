pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t maddularoopeshreddy/abinay:bus .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push maddularoopeshreddy/abinay:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus -p 8888:80 maddularoopeshreddy/abinay:bus'
            }
        }
    }
}
