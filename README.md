# Project-Udacity-3
URL - http://3.88.132.238:30080/
![Web-URL-Nodeport-page](https://github.com/user-attachments/assets/a58346b3-b6d2-4abd-a8e8-29676ebfb811)


Task 1 - 


1.) Created IAM Role for codebuild.

2.) Refer buildspec.yml for the each and evry stage to create docker image 

3.) Tag the image 

4.) Push the Docker image to AWS ECR

![CodeBuild-Pipeline-3](https://github.com/user-attachments/assets/ee47c3c2-ada1-4766-a6e3-0eb5001f9cb2)

5.) AWS Code connections added in order to run the codebuild on a Git PUSH

![image](https://github.com/user-attachments/assets/ccf9a260-7bf9-49c9-ba80-6a263f99fc59)


Task 2 -

1.) Minkube cluster creation

![image](https://github.com/user-attachments/assets/f51c01b3-a06f-4e47-9b14-d8a8a24fc5a2)


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

![Kubectl DB postgres SS](https://github.com/user-attachments/assets/699c6a89-3c6e-4fb6-bf69-8485246d5c55)


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


Cloud watch commands - 

kubectl create namespace logging

kubectl apply -f fluent-bit-configmap.yaml

kubectl apply -f fluent-bit-daemonset.yaml

kubectl get serviceaccount fluent-bit-sa -n logging -o yaml

![image](https://github.com/user-attachments/assets/5fdd2c7e-19a6-40b7-81f7-2d8c3ed9ab05)

Please see the cloud watch application logs 

![image](https://github.com/user-attachments/assets/c51827d7-8720-43b7-bae2-42364c3c7737)


![image](https://github.com/user-attachments/assets/ff5e4749-8d53-4267-b200-f0ad0fbcad40)


![image](https://github.com/user-attachments/assets/65b2db41-bdac-4086-9046-db0e6e279c4d)


kubectl get pods -n logging

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


