To Install Minikube:-
https://minikube.sigs.k8s.io/docs/start/

#Start the minikube

minikube start 

#install the ingress controller addons : Check all addons features by running : minikube addons list
minikube addons enable ingress

#Build the docker images and push to container registry:-
#Clone the repo to make use of the Dockerfile and index.html to display the custom msg
docker build -t weba:v1 .
docker tag weba:v1 hitesharora1116/weba:v1
docker push hitesharora1116/weba:v1

#Apply the manifest files 

kubectl apply -f deployment.yaml #Run 2replicas of weba and webb 'nginx' pods with 2 replicas, images are pulled from public hitesharora1116/ repositories
kubectl apply -f service.yaml    #expose the application 
kubectl apply -f ingress.yaml    #deploy ingress rules 

kubectl get ingress  (this may take some time to display address. this address equals minikube ip)

Get the minikube ip using minikube ip (usually it is 192.168.49.2)
update the /etc/hosts file with the ip and hostname like hellojfrog.info

Finally, in the browser, search for  hellojfrog.info
