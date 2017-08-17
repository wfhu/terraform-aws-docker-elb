# terraform-aws-docker-elb
use terraform to deploy a basic aws infrastructure with simple web service running in docker

* to deploy this demo infrastructure, you need to write your AWS_ACCESS_KEY and AWS_SECRET_KEY in terraform.tfvars or INPUT manually when you run terraform apply
```
# cat terraform.tfvars 
access_key = "Your-ACCESS-key"
secret_key = "Your-Secret-key for AWS xxxxxxxxxx"
```








the whole project is inspired and updated from https://www.airpair.com/aws/posts/ntiered-aws-docker-terraform-guide
