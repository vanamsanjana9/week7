pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker Image...'
                bat 'docker build -t mypythonflaskapp .'
            }
        }

        stage('Run') {
            steps {
                echo 'Running Docker Container...'

                // Remove old container if it exists
                bat 'docker rm -f mycontainer 2>nul || exit /b 0'

                // Run the new container
                bat 'docker run -d -p 5000:5000 --name mycontainer mypythonflaskapp'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Please check the Jenkins logs.'
        }
    }
}