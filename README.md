# security-operations-task
1. cd to the project directory and create the ecr repo attaching an appropriate inline policy as stated in main.tf
>terraform init
>terraform plan
Check the changes to deploy and then
>terrform apply
2. cd to the rates folder and build the docker image with tag including the aws account id and ecr repo name created in the previous step
>cd rates
>docker build -t aws_account_id.dkr.ecr.region.amazonaws.com/ecr-repo-name .  
3. pipe the ecr login token to docker and push the docker image to ecr
>aws ecr get-login-password --region region | docker login --username AWS --password-stdin aws_account_id.dkr.ecr.region.amazonaws.com 
>docker push aws_account_id.dkr.ecr.us-east-1.amazonaws.com/ecr-repo-name     
4. To run the app, we pull the docker image from ECR and execute
>docker pull aws_account_id.dkr.ecr.region.amazonaws.com/ecr-repo-name:latest
>docker run -dp 127.0.0.1:3000:3000  aws_account_id.dkr.ecr.region.amazonaws.com/ecr-repo-name               