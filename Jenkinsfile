pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t maddularoopeshreddy/projects:train .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push maddularoopeshreddy/projects:train'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 9999:80 maddularoopeshreddy/projects:train'
            }
        }
    }
}
