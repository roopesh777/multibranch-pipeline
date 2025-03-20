pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t maddularoopeshreddy/projects:bus .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push maddularoopeshreddy/projects:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus -p 8888:80 maddularoopeshreddy/projects:bus'
            }
        }
    }
}
