pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Yogeshpisal216/flask-redis-project.git'
            }
        }    

        stage('Build') {
            steps {
                sh '''
                    docker build -t flask-redis .
                    docker tag flask-redis:latest yogi2112/flask-redis:latest
                '''
            }
        }

        stage('Push') {
            steps {
                sh '''
                    docker push yogi2112/flask-redis:latest
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    kubectl apply -f k8s/namespace.yaml
                    kubectl apply -f k8s/redis-deployment.yaml
                    kubectl apply -f k8s/redis-service.yaml
                    kubectl apply -f k8s/flask-deployment.yaml
                    kubectl apply -f k8s/flask-service.yaml

                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    kubectl get all -n flask-redis
                   '''
            }
        }
    }
}





