pipeline {
    agent { label 'agent01' }

    environment {
        AWS_ACCOUNT_ID = '107895200189'
        AWS_DEFAULT_REGION = 'us-east-1' 
        REPO_NAME = 'zivgl66/pythonapp' 
        IMAGE_TAG = "${env.BUILD_ID}" 
        DOCKER_IMAGE = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${REPO_NAME}:${IMAGE_TAG}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Zivgl66/example-python-web-app'
            }
        }

        stage('Login to AWS ECR') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'aws-ecr-credentials', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        sh """
                            aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID
                            aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY
                            aws configure set default.region $AWS_DEFAULT_REGION
                            eval \$(aws ecr get-login-password --region ${AWS_DEFAULT_REGION}) | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${REPO_NAME}
                        """
                    }
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "sudo docker build -t ${DOCKER_IMAGE} ."
                }
            }
        }

        stage('Push Docker Image to ECR') {
            steps {
                script {
                    sh "sudo docker push ${DOCKER_IMAGE}"
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}