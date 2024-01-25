PROJECT 1: Provisioning AWS RDS with Terraform


![terraform](https://github.com/sindhuk02/AWS_RDS_USING_TERRAFORM/assets/157628894/248b2645-8faa-42c1-95bb-7ee1cd24634c)

STEPS TO CREATE AWS RDS :

1.Create an EC2 instance in AWS console, I create an instance with name TERRAFORM

2.Login into Putty terminal with public -IP and keypair of that instance

3.After login to centos root user, install Terraform and its supporting packages with linux script
 sudo yum update -y 
 sudo yum install -y yum-utils 
 sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo 
 sudo yum -y install terraform 
4.After execution above commands, we installed Terraform and its supporting packages, from the above link we downloaded HASHICORP LANGUAGE packages

5.After installation create a directory with command mkdir<directory_name> and go to that directory with command cd < directory_name >.
6.Create a file name variable.tf and provide the variables for your RDS instance in a variables.tf file using HCL script mentioned below. Some variables that are included are      the database engine, instance size, storage size, username and password, and backup retention period. Create that file with the command vi variable.tf. it automatically          created and entered into that file by entering “I” (insert) the variables script mentioned in the below picture. I had entered my configurations in that script as variables.     For access_key and secret_key we have to create a IAM user with suitable permission and generate access_key and secret_key for that IAM user , paste this keys in the variable    file script and save it.
7.create a file variable.tf and save the following script in the file

variable "access_key" { description = "AWS access key" type = string default = "AKIATX6ULZXLPSOT7VHR" }

variable "secret_key" { description = "AWS secret key" type = string default = "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" } variable "db_engine" { description = "Database engine type" type = string default = "mysql" }

variable "db_instance_class" { description = "Database instance class" type = string default = "db.t2.micro" }

variable "allocated_storage" { description = "Allocated storage for the RDS instance (in GB)" type = number default = 20 }

variable "username" { description = "Username for the RDS instance" type = string default = "admin" }

variable "password" { description = "Password for the RDS instance" type = string default = "admin123" }

variable "backup_retention_period" { description = "Backup retention period in days" type = number default = 7 }

