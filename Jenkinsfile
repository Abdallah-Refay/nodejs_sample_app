pipeline {
    agent {
        label 'private2'
    }

    stages {
        stage('clone rds_redis branch') {
            steps {
                git branch: 'rds_redis',
                    url: 'https://github.com/Abdallah-Refay/nodejs_sample_app.git'
            }
        }
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