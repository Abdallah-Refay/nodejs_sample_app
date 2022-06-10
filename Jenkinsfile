pipeline {
    agent {
        label ('private1 && private2')
    }

    stages {
        stage('building and running the docker file') {
            steps {
                sh '''
                docker build -f dockerfile . -t node_app:latest
                docker rm -f app
                docker run --env-file /home/ubuntu/.env -d --name app -p 3000:3000 node_app:latest
                '''
            }
        }
    }
}
