# Ansible

### Prerequisites
- 3 EC2 Instances 
    - 2 using Terraform
    - 1 Manually
    - You can use which ever approach you are comfortable with

- EC2 Keys - `ls ~/aws/aws_keys/default-ec2.pem`

- AWS CLI - `aws configure`
```sh
# or
export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**************
```

- boto3 and botocore - For EC2 Dynamic Inventory and Creating EC2 Instances
```sh
# TEst
python
# boto3 quick start
> import boto3
> client = boto3.client('ec2')
```

### Create EC2 Instances using Terraform

```
cd terraform/backup/09-multiple-ec2-instances
export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**************
terraform init
terraform apply
ls ~/aws/aws_keys/ # Make sure that the keys file is present
```

### Ansible Commands

```
ansible --version
ansible -m ping all
ansible all -a "whoami"
ansible all -a "uname"
ssh -vvv -i ~/aws/aws_keys/default-ec2.pem ec2-user@3.83.104.44
ls ~/aws/aws_keys/default-ec2.pem
chmod 400 /Users/rangaraokaranam/aws/aws_keys/default-ec2.pem
ansible all -a "uname"
ansible all -a "uname -a"
ansible all -a "pwd"
ansible all -a "python --version"
ansible dev -a "python --version"
ansible qa -a "python --version"
ansible first -a "python --version"
ansible groupofgroups -a "python --version"
ansible devsubset -a "python --version"
ansible --list-host all
ansible --list-host dev
ansible --list-host first
ansible --list-host \!first
ansible --list-host qa:dev
ansible-playbook filename.yml
ansible-playbook filename.yml -e variable1=CommandLineValue
ansible-playbook filename.yml --list-tasks
ansible-playbook filename.yml --list-hosts
ansible-playbook filename.yml --list-tags
ansible-playbook -l dev filename.yml 
ansible-inventory --list
ansible-inventory --graph

```
