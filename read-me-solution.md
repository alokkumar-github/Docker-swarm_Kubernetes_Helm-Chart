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
kubectl get nodes
kubectl describe node  minikube
kubectl get all --all-namespaces
kubectl get pods --all-namespaces
kubectl get all -n monitoring
kubectl edit -n monitoring service/monitoring-grafana    - to  edit pod yaml ex. to change ClusterIP to NodePort
export EDITOR=nano
kubectl delete deploy mongodb
kubectl logs pod  mongodb-5995d6db7f-bhfrz
kubectl delete pod mongodb-5995d6db7f-sd2x2
kubectl describe pod mongodb-5995d6db7f-sd2x2 
helm install --name monitoring --namespace monitoring stable/prometheus-operator

-------- install helm --------------------- get gz , tar it , move to /usr/local/bin, then delete all the tar,untar file
wget https://get.helm.sh/helm-v2.14.3-linux-amd64.tar.gz
tar zxvf helm-v2.14.3-linux-amd64.tar.gz 
sudo mv linux-amd64/helm /usr/local/bin
rm helm-v2.14.3-linux-amd64.tar.gz
rm -rf ./linux-amd64/
kubectl delete namespace monitoring

---------- hom much usage memory usage ie profiling of container, pods, cluster-------------------

minikube addons list
minikube addons enable metrics-server
kubrctl top pod
kubrctl top node

minikube dashboard

while true; crul minkibeip:port/api; echo; done

kubectl get po --watch
kubectl get rolebinding
kubectl describe rolebinding <rolebinding-name>









