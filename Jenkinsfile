pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'ap-south-1'
    }

    stages {
        stage('Prepare') {
            steps {
                echo 'Preparing...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('List AWS Glue Jobs') {
            steps {
                script {
                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 's3Test']]) {
                        echo 'Listing AWS Glue jobs...'
                        bat 'aws glue get-jobs'
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
