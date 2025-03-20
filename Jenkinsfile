pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t maddularoopeshreddy/projects:bank .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh 'docker push maddularoopeshreddy/projects:bank'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank2 -p 4455:80 maddularoopeshreddy/projects:bank'
            }
        }
    }
}
