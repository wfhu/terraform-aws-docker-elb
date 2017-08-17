# terraform-aws-docker-elb
use terraform to deploy a basic aws infrastructure with simple web service running in docker

Deploy web service with nginx:alpine in docker within two EC2 instancse in private subnet, one EC2 instance in public subnet as nat server for ssh access to EC2 instances in the private subnet, one internet-facing ELB to load balance the web service between the two EC2, all in a VPC environment.

* to deploy this demo infrastructure, you need to write your AWS_ACCESS_KEY and AWS_SECRET_KEY in terraform.tfvars or INPUT manually when you run terraform apply
```
# cat terraform.tfvars 
access_key = "Your-ACCESS-key"
secret_key = "Your-Secret-key for AWS xxxxxxxxxx"
```


## Installation 
How to install terraform you can find [here](https://www.terraform.io/intro/getting-started/install.html). Or you can using a Docker image to keep your environment clear. For example, [this one](https://hub.docker.com/r/amontaigu/terraform/).

## Preparations
### AWS account 
If you don't have account, you may get a free AWS account. In the setup will be used free t2.micro instances. 
#### SSH keys
Before to start, create ssh keys in *ssh/* directory. Terraform will create key-pair in AWS, based on these keys. See [how to create ssh keys](https://confluence.atlassian.com/bitbucketserver/creating-ssh-keys-776639788.html)
Create a pem file with private ssh key you generated. Terraform will need to the pem file to connect to instances for provisioning.
#### Update the project file with new information
There are three file need your credentials for successing run up. First of all, update *key-pairs.tf* set there a path to the public ssh key, generated earlier. In *variables.tf* update your AWS account information. In *nat-server.tf* update connection block for each resources, set there the path to ssh private key.    

## How to use
After all configuration files are ready, you can do check if there are no mistakes.
```
terraform plan
```
This command will show either syntax errors or list of resources will be created. After you can run:
```
terraform apply
```
This command will build and run all resources in the *.tf files. If you run this command many times, Terraform will destroy previous instances before creating new ones. 
That is it. Now you have fully functioned docker swarm cluster in AWS.

If you want to terminate instances and destroy the configuration you may call:
```
terraform destroy
```






PS: the whole project is inspired and updated from https://www.airpair.com/aws/posts/ntiered-aws-docker-terraform-guide , I have tested it several times, everything just works as expected.
