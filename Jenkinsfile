pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Deploy to DockerHub') {
            when {
                branch 'dev'
            }
            steps {
                echo "Pushing Docker image..."
                sh """
                    docker login -u ${DOCKERHUB_CREDENTIALS_USR} -p ${DOCKERHUB_CREDENTIALS_PSW}
                    docker build -t milagjorgoska/jenkins-test .
                    docker push milagjorgoska/jenkins-test
                """
            }
        }
    }
}
