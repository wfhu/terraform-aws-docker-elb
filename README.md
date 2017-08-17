# terraform-aws-docker-elb
use terraform to deploy a basic aws infrastructure with simple web service running in docker

Deploy web service with nginx:alpine in docker within two EC2 instancse in private subnet, one EC2 instance in public subnet as nat server for ssh access to EC2 instances in the private subnet, one internet-facing ELB to load balance the web service between the two EC2, all in a VPC environment.

* to deploy this demo infrastructure, you need to write your AWS_ACCESS_KEY and AWS_SECRET_KEY in terraform.tfvars or INPUT manually when you run terraform apply
```
# cat terraform.tfvars 
access_key = "Your-ACCESS-key"
secret_key = "Your-Secret-key for AWS xxxxxxxxxx"
```








the whole project is inspired and updated from https://www.airpair.com/aws/posts/ntiered-aws-docker-terraform-guide
