# Kuberentes Challenge

1. clone the kubernetes challenge repo.
    
    git clone https://github.com/learnk8s/kubernetes-challenge && cd kubernetes-challenge

2. build the docker image and push image to a image registry. we ll be using docker hub as an image registry. Make sure you have a docker hub account before proceeding

    # build application image
    docker build . -t docker.io/<username>/myname-nodejs

    # enter credentials for your own docker hub account
    docker login 

    # push application image to hub
    docker push . -t docker.io/<username>/myname-nodejs

3. Start your local minikube and enable ingress controller for exposing the app.

    minikube start
    minikube addons enable ingress

4. Create the k8s resources using cli.

    kubectl create deployment myname-nodejs --image=mumustafa/myname-nodejs --port=4000 --dry-run=client -o yaml > .\k8s-manifests\deployment.yaml
    
    kubectl create cm candidate-name --from-literal="NAME=Mustafa"

    kubectl expose deployment myname-nodejs --port=80 --target-port=4000 --type=NodePort

    kubectl create ingress myname-nodejs --class=nginx --rule="/=myname-nodejs:80" --annotation=nginx.ingress.kubernetes.io/rewrite-target=/

kubectl run busybox --image=