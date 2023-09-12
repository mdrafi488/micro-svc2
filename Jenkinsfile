pipeline {
    agent any

    stages {
        stage('CI ') {
            steps {
                sh '''
                # Docker Login
                aws ecr get-login-password --region ap-south-1 | sudo docker login --username AWS --password-stdin 719648668301.dkr.ecr.ap-south-1.amazonaws.com
                # Docker Build
                sudo docker build -t 719648668301.dkr.ecr.ap-south-1.amazonaws.com/static:$BUILD_NUMBER .
                # Docker Push
                sudo docker push 719648668301.dkr.ecr.ap-south-1.amazonaws.com/static:$BUILD_NUMBER
                '''
            }
        }
        stage('CD Stage') {
            steps {
                sh '''
                cd k8s/
                kubectl apply -f . 
                '''
            }
        }
        // stage('Validation stage') {
        //     steps {
                
        //         sh 'kubectl get nodes'
        //         sh 'kubectl get pods -A'
                
        //     }
        // }
        
    }
}
