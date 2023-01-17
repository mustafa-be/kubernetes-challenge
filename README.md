# Kuberentes Challenge

1. Clone the kubernetes challenge repo.
    
        git clone https://github.com/learnk8s/kubernetes-challenge && cd kubernetes-challenge

2. Start your local minikube and enable ingress controller for exposing the app.

        minikube start
        minikube addons enable ingress

3. Enable minikube docker registry, build the docker image. 

        eval $(minikube docker-env)
        docker build . -t nodejs-app

4. Create the k8s resources using cli.

        kubectl create ns kubernetes-challenge
        kubectl apply -f k8s-manifests/
    
5. Run the following command to see if your app is exposed.

        curl $(minikube ip)
