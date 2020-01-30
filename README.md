# cfgmgmt-terraform-localstack

A quick demo of using Localstack to "mock the internet" and pretend to be AWS

### running the demo

```
export AWS_ACCESS_KEY_ID='123'
export AWS_SECRET_ACCESS_KEY='xyz'
export AWS_BUCKET_NAME='demo-bucket'
export AWS_BUCKET_REGION='us-east-1'
docker-compose up -d
terraform init
terraform apply
open http://localhost:4572/
open http://localhost:8080/#/infra
aws s3 --endpoint-url=http://localhost:4572 cp "config-management-camp.png" s3://demo-bucket-terraform
curl http://localhost:4572/demo-bucket-terraform/config-management-camp.png | imgcat
```
