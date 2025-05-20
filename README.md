# Project-Udacity-3

Task 1 - 
1.) Created IAM Role for codebuild.
2.) Refer buildspec.yml for the each and evry stage to create docker image 
3.) Tag the image 
4.) Push the Docker image to AWS ECR

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


