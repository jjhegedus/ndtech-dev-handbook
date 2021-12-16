# Introduction 
ndtech-dev-handbook is a handbook for development of ndtech assets. One of the key things it provides is a location to securely store secrets that an ndtech developer can use to access ndtech assets. These are very securely managed. 

# Contribute
This is my personal repo at the moment but I may open it to the inner circle if such circle ever materializes

# Digital Ocean
## build container
docker build --force-rm -f "digital-ocean/dockerfile" -t prod-do-ndtech-k8s-cluster:latest --build-arg CONTEXT_PATH=/root .

## launch container for debug
docker run --rm -v ${PWD}:/usr/src -e NDTECH_K8S_MODE="debug" -e RELATIVE_PROCESSING_PATH="digital-ocean/" -e AWS_ACCESS_KEY_ID="$($aws_access_key_id."Access key ID")" -e AWS_SECRET_ACCESS_KEY="$($aws_secret_access_key."Secret access key")" -e AWS_DEFAULT_REGION="us-west-2" -e CONTEXT_PATH=/root -e DIGITAL_OCEAN_INITIAL_TOKEN="$Env:DIGITAL_OCEAN_INITIAL_TOKEN" -e JX_VALUE_ADMINUSER_PASSWORD=$ENV:JX_VALUE_ADMINUSER_PASSWORD -e JX_VALUE_PIPELINEUSER_USERNAME=$ENV:JX_VALUE_PIPELINEUSER_USERNAME -e JX_NO_DELETE_TMP_DIR=true -e JX_VALUE_PIPELINEUSER_EMAIL=$ENV:JX_VALUE_PIPELINEUSER_EMAIL -e JX_VALUE_PIPELINEUSER_TOKEN=$ENV:JX_VALUE_PIPELINEUSER_TOKEN -it --entrypoint /bin/bash prod-do-ndtech-k8s-cluster:latest

## launch container to create cluster
docker run --rm -v ${PWD}:/usr/src -e NDTECH_K8S_MODE="create-cluster" -e RELATIVE_PROCESSING_PATH="digital-ocean/" -e 
AWS_ACCESS_KEY_ID="$($aws_access_key_id."Access key ID")" -e AWS_SECRET_ACCESS_KEY="$($aws_secret_access_key."Secret access key")" -e AWS_DEFAULT_REGION="us-west-2" -e CONTEXT_PATH=/root -e DIGITAL_OCEAN_INITIAL_TOKEN="$Env:DIGITAL_OCEAN_INITIAL_TOKEN" -e JX_VALUE_ADMINUSER_PASSWORD=$ENV:JX_VALUE_ADMINUSER_PASSWORD -e JX_VALUE_PIPELINEUSER_USERNAME=$ENV:JX_VALUE_PIPELINEUSER_USERNAME -e JX_NO_DELETE_TMP_DIR=true -e JX_VALUE_PIPELINEUSER_EMAIL=$ENV:JX_VALUE_PIPELINEUSER_EMAIL -e JX_VALUE_PIPELINEUSER_TOKEN=$ENV:JX_VALUE_PIPELINEUSER_TOKEN prod-do-ndtech-k8s-cluster:latest

## launch container to destroy cluster
docker run --rm -v ${PWD}:/usr/src -e NDTECH_K8S_MODE="destroy-cluster" -e RELATIVE_PROCESSING_PATH="digital-ocean/" -e 
AWS_ACCESS_KEY_ID="$($aws_access_key_id."Access key ID")" -e AWS_SECRET_ACCESS_KEY="$($aws_secret_access_key."Secret access key")" -e AWS_DEFAULT_REGION="us-west-2" -e CONTEXT_PATH=/root -e DIGITAL_OCEAN_INITIAL_TOKEN="$Env:DIGITAL_OCEAN_INITIAL_TOKEN" -e JX_VALUE_ADMINUSER_PASSWORD=$ENV:JX_VALUE_ADMINUSER_PASSWORD -e JX_VALUE_PIPELINEUSER_USERNAME=$ENV:JX_VALUE_PIPELINEUSER_USERNAME -e JX_NO_DELETE_TMP_DIR=true -e JX_VALUE_PIPELINEUSER_EMAIL=$ENV:JX_VALUE_PIPELINEUSER_EMAIL -e JX_VALUE_PIPELINEUSER_TOKEN=$ENV:JX_VALUE_PIPELINEUSER_TOKEN prod-do-ndtech-k8s-cluster:latest

# Bash Scripting
## Append data to a text file by typing the text
cat >>test.txt

## Append data to a text file using a here document
cat > ./test.txt << EOF; $(echo)
http://dl-cdn.alpinelinux.org/alpine/v$(cat /etc/alpine-release | cut -d'.' -f1,2)/main
http://dl-cdn.alpinelinux.org/alpine/v$(cat /etc/alpine-release | cut -d'.' -f1,2)/community
http://dl-cdn.alpinelinux.org/alpine/edge/community
EOF

# Alpine
## Alpine edge community repo
http://dl-cdn.alpinelinux.org/alpine/edge/community

# Powershell
## Tee-Object - https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7
### Output processes to a file and to the console
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
