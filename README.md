# Project-Udacity-3
URL - http://54.205.142.199:30080/
![Web-URL-Nodeport-page](https://github.com/user-attachments/assets/a58346b3-b6d2-4abd-a8e8-29676ebfb811)


Task 1 - 


1.) Created IAM Role for codebuild.

2.) Refer buildspec.yml for the each and evry stage to create docker image 

3.) Tag the image 

4.) Push the Docker image to AWS ECR

![CodeBuild-Pipeline-3](https://github.com/user-attachments/assets/ee47c3c2-ada1-4766-a6e3-0eb5001f9cb2)


Task 2 -

1.) Minkube cluster creation


2.) run yaml 

-- --- --- kubectl apply -f postgres-secrets.yml


-- --- --- kubectl apply -f postgres-config.yml


-- --- --- kubectl apply -f postgres-pv.yml


-- --- --- kubectl apply -f postgres-pvc.yml


-- --- --- kubectl apply -f postgres-deployment.yml

-- --- --- kubectl apply -f postgres-service.yml

-- --- --- kubectl apply -f app-secrets.yml

-- --- --- kubectl apply -f app-config.yml

-- --- --- kubectl apply -f app-deployment.yml

-- --- --- kubectl apply -f app-service.yml

NAME                                 READY   STATUS    RESTARTS   AGE

postgres-6fd9668ccf-dgphh            1/1     Running   0          4m50s

project-udacity-3-7d98c598b9-8dx4l   1/1     Running   0          4m13s

ubuntu@ip-172-31-94-117:~/deployment$ kubectl get svc
NAME                TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE

kubernetes          ClusterIP   10.96.0.1        <none>        443/TCP          8m18s

postgres            ClusterIP   10.110.157.243   <none>        5432/TCP         4m50s

project-udacity-3   NodePort    10.96.200.226    <none>        8080:30080/TCP   3m52s

Screenshots - 
![EC2-Black-1-Minikube-resources](https://github.com/user-attachments/assets/fb627072-8d86-45be-9e6d-4d66b2f2ee29)
![Describe svc postgres](https://github.com/user-attachments/assets/991fb4b2-a297-466b-9eff-4c59f89eb51d)
![Describe deploy service](https://github.com/user-attachments/assets/d615bae8-0b8d-4436-84cc-d0e2f6951acf)



Issues -

solution - 
1.)
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ****.dkr.ecr.us-east-1.amazonaws.com

2.) 
kubectl create secret docker-registry ecr-registry \
  --docker-server=******.dkr.ecr.us-east-1.amazonaws.com \
  --docker-username=AWS \
  --docker-password=$(aws ecr get-login-password --region us-east-1) \
  --docker-email=******@gmail.com


