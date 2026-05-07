pipeline {
    agent any

    environment {
        AWS_REGION = "ap-south-1"
        ECR_REPO = "010438490109.dkr.ecr.ap-south-1.amazonaws.com/api-dev"
        IMAGE_TAG = "${env.BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: "${env.BRANCH_NAME}", url: "https://gitlab.com/lezinhere/devsecops-assessment.git"
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=api \
                    -Dsonar.sources=api
                    '''
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                cd api
                docker build -t api:${IMAGE_TAG} .
                '''
            }
        }

        stage('Tag Image') {
            steps {
                sh '''
                docker tag api:${IMAGE_TAG} ${ECR_REPO}:${IMAGE_TAG}
                '''
            }
        }

        stage('Login to ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin 010438490109.dkr.ecr.ap-south-1.amazonaws.com
                '''
            }
        }

        stage('Push Image') {
            steps {
                sh '''
                docker push ${ECR_REPO}:${IMAGE_TAG}
                '''
            }
        }

        stage('Update Helm') {
            steps {
                sh '''
                cd ~/application-helm-charts/api
                sed -i "s/tag:.*/tag: \\"${IMAGE_TAG}\\"/" values.yaml
                git add .
                git commit -m "update api image ${IMAGE_TAG}"
                git push origin main
                '''
            }
        }
    }
}
