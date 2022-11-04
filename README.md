Terraform Module to provision an EC2 Instance that is running Apache.

Not intended for production use. 


```hcl
terraform {

}

provider "aws" {
  region = "eu-west-1"
}

module "apache" {
        source        = ".//terraform-aws-apache-example"
        vpc_id        = "vpc-0000000000"
        my_ip         = "MY_OWN_IP_ADDRESS/32"
        public_key    = "ssh-rsa AAAAB..."
        instance_type = "t2.micro"
        server_name   = "Apache Server"
}

output "public_ip" {
  value = module.apache.public_ip
}