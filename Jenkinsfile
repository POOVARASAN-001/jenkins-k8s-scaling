
pipeline {
    agent any

    environment {
        KUBECTL = 'D:\\DockerApp\\resources\\bin\\kubectl.exe'
        KUBECONFIG = 'C:\\Users\\POOVARASAN\\.kube\\config'
    }

    stages {
        stage('Create Deployment') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
            }
        }

        stage('Scale to Three Replicas') {
            steps {
                bat '"%KUBECTL%" scale deployment/scaling-app --replicas=3'
            }
        }

        stage('Verify Scaling') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/scaling-app --timeout=120s'
                bat '"%KUBECTL%" get deployment scaling-app'
                bat '"%KUBECTL%" get pods -l app=scaling-app'
            }
        }
    }
}
