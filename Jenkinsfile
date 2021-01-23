pipeline {
    environment {
        registry = 'sourish88/sample-java-app'
        registryCredential = 'DockerHub-Creds'
    }
    
    agent {
        label 'local'
    }

    parameters {
        string(name: 'APP_NAME',  defaultValue: '',  description: 'Name of the container', trim: true)
        string(name: 'DOCKER_REPO',  defaultValue: '',  description: 'Docker repository', trim: true)
        string(name: 'VERSION_TAG',  defaultValue: '',  description: 'Docker image tag', trim: true)
    }

    stages {
        // Deployment stage
        stage('Deploy') {
            steps {
                bat """
                docker rm $APP_NAME
                docker run -d --name $APP_NAME -p 8081:8080 $DOCKER_REPO:$VERSION_TAG
                """
            }
        }
    }
}