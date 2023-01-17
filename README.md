# Kuberentes Challenge

1. clone the kubernetes challenge repo.
    
    git clone https://github.com/learnk8s/kubernetes-challenge && cd kubernetes-challenge

2. build the docker image and push image to a minikube docker image registry.

    # enable minikube docker registry
    eval $(minkube docker-env)

    # build application image
    docker build . -t <username>/myname-nodejs

3. Start your local minikube and enable ingress controller for exposing the app.

    minikube start
    minikube addons enable ingress

4. Create the k8s resources using cli.

    kubectl create ns kubernetes-challenge     
    
    kubectl apply -f k8s-manifests/
    