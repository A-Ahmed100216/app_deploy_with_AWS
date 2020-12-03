# Deploy the app to Jenkins

## Introduction
Implement the CD aspect of CI by deploying the app to Jenkins.

## Pre-Requisites
* Git
* AWS
* Working app

## Instructions
1. Create a new repository in GitHub
2. In Jenkins, create a new job
3. Following the generic configuration until the 'Build Environment' stage.




rsync -avz -e "ssh -o StrictHostKeyChecking=no -i $AWS_ACCESS" -a . ubuntu@34.241.141.192:~/
ssh -o "StrictHostKeyChecking=no" -i $AWS_ACCESS ubuntu@34.241.141.192 <<EOF
pm2 restart app
EOF
