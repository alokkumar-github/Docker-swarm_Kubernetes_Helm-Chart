https://stackoverflow.com/questions/52645473/coredns-fails-to-run-in-kubernetes-cluster

sudo dpkg -l | grep virtualbox
sudo  apt-get purge virtualbox-6.0 virtualbox-ext-pack  to  uninstall minikube
cat ~/.minikube/config/config.json   to configue memeory and cps to minikube
env
minikube start
minikube staus
kubectl cluster-info
kubectl delete -f .
kubectl apply -f .

