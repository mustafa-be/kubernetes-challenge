# Kuberentes Challenge

1. clone the kubernetes challenge repo.
    
    git clone https://github.com/learnk8s/kubernetes-challenge && cd kubernetes-challenge

2. enable minikube docker registry, build the docker image. 

    eval $(minkube docker-env)

    docker build . -t <username>/nodejs-app

3. Start your local minikube and enable ingress controller for exposing the app.

    minikube start
    minikube addons enable ingress

4. Create the k8s resources using cli.

    kubectl create ns kubernetes-challenge     
    
    kubectl apply -f k8s-manifests/
    