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
4. Select the 'Use secret text(s) or file(s)' option. Set the 'Key File Variable' as a variable name such as 'AWS ACCESS'
5. Add the credentials which is the AWS key created during instance launch. Copy this key and save.
6. Build --> Select 'Execute Shell'  and add the following commands. This will automate authetnication to obtain access to the instance.
```bash
rsync -avz -e "ssh -o StrictHostKeyChecking=no -i $AWS_ACCESS" -a . ubuntu@34.241.141.192:~/
ssh -o "StrictHostKeyChecking=no" -i $AWS_ACCESS ubuntu@34.241.141.192 << EOF
pm2 restart app --update-env
EOF
```
7. Post- Build Actions --> Select 'Git Publisher' and configure.
8. Save
9. Push to Dev bracnh to trigger a build 
