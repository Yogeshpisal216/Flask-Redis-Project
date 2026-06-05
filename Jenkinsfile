pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Yogeshpisal216/Flask-Redis-Project.git'
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

		withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
			
                sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    docker push yogi2112/flask-redis:latest
                '''
                  }
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





