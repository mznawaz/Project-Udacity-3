# Project-Udacity-3

Task 1 - 
1.) Created IAM Role for codebuild.
2.) Refer buildspec.yml for the each and evry stage to create docker image 
3.) Tag the image 
4.) Push the Docker image to AWS ECR

Task 2 -

1.) Minkube cluster creation
2.) run yaml 

ubuntu@ip-172-31-94-117:~/deployment$ ls -lrt
total 44
-rw-rw-r-- 1 ubuntu docker  221 May 19 09:02 postgres-service.yml
-rw-rw-r-- 1 ubuntu docker  157 May 19 09:02 app-config.yml
-rw-rw-r-- 1 ubuntu docker  161 May 19 09:02 app-secrets.yml
-rw-rw-r-- 1 ubuntu docker 1664 May 19 09:02 postgres-deployment.yml
-rw-rw-r-- 1 ubuntu docker  129 May 19 09:02 postgres-config.yml
-rw-rw-r-- 1 ubuntu docker  171 May 19 09:02 postgres-pvc.yml
-rw-rw-r-- 1 ubuntu docker  190 May 19 09:02 postgres-pv.yml
-rw-rw-r-- 1 ubuntu docker  182 May 19 09:02 postgres-secrets.yml
-rw-rw-r-- 1 ubuntu docker  308 May 20 16:59 app-service.yml
-rw-rw-r-- 1 ubuntu ubuntu 2085 May 20 17:07 app-deployment.yml_correct
-rw-rw-r-- 1 ubuntu ubuntu 2086 May 20 18:07 app-deployment.yml
ubuntu@ip-172-31-94-117:~/deployment$ kubectl get po
NAME                                 READY   STATUS    RESTARTS   AGE
postgres-6fd9668ccf-dgphh            1/1     Running   0          4m50s
project-udacity-3-7d98c598b9-8dx4l   1/1     Running   0          4m13s
ubuntu@ip-172-31-94-117:~/deployment$ kubectl get svc
NAME                TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
kubernetes          ClusterIP   10.96.0.1        <none>        443/TCP          8m18s
postgres            ClusterIP   10.110.157.243   <none>        5432/TCP         4m50s
project-udacity-3   NodePort    10.96.200.226    <none>        8080:30080/TCP   3m52s
ubuntu@ip-172-31-94-117:~/deployment$ kubectl get secrets
NAME                  TYPE                                  DATA   AGE
app-secrets           Opaque                                3      4m49s
default-token-zlh8z   kubernetes.io/service-account-token   3      8m10s
ecr-registry          kubernetes.io/dockerconfigjson        1      5m38s
postgres-secrets      Opaque                                2      5m26s
ubuntu@ip-172-31-94-117:~/deployment$ kubectl get config
error: the server doesn't have a resource type "config"
ubuntu@ip-172-31-94-117:~/deployment$ kubectl get configmap
NAME               DATA   AGE
app-config         4      4m55s
kube-root-ca.crt   1      8m22s
postgres-config    2      5m30s
ubuntu@ip-172-31-94-117:~/deployment$ minikube ip
172.31.94.117
ubuntu@ip-172-31-94-117:~/deployment$

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


