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

                bat 'docker rm -f mycontainer 2>nul || exit /b 0'

                bat 'docker run -d -p 5001:5000 --name mycontainer mypythonflaskapp'
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
