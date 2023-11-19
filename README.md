# myrepo01


Step1: To build an docker image using docker file.
Step2: Tag the docker image as kv1.
COMMAND : docker build -t booking system(image name):kv1(tag)
Step3: Pull the builded docker image to the dockerhub.
COMMAND : docker push hariharankube(namespace)/bookingsystem(repository):kv1(tag)
Step4: Install docker desktop and enable kubernetes
COMMAND : kubectl get node 
Step5: Deploy the Web and Database files on kuberenetes cluster (Modify the image on the deployment files)
COMMAND: kubectl create -f booking-system-web-deployment.yaml  
         kubectl create -f booking-system-db-deployment.yaml
st
