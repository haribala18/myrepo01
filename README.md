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
Step6: Expose the service with LoadBalancer
COMMAND: kubectl port-forward svc/booking-system-service 8080:80 
         kubectl expose svc booking-system-service --name booking-system-service-lb --port=80 --target-port=80 --type=LoadBalancer
Step7: To get inside the pod change the directory into tmp and inject the SQL file data on DB
COMMAND: kubectl exec -it pod/booking-system-db-76d94778b5-hsk7v -- bash
         mariadb -u root -p booking_system < booking_system.sql
         kubectl cp booking_system.sql booking-system-db-76d94778b5-hsk7v :/tmp/
Step8: Ensure Application fuctionality.
