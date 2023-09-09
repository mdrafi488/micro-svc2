ci:
    aws ecr login
    docker build -t imagename:tag
    docker push imagename:tag
cd:
    kubectl apply -f deployment.yaml service.yaml ingress.yaml