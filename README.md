# Launch_EC2_Instance_With_Ansible
🌐 Ansible Playbook to create EC2 Instance in AWS🌏

Introduction:
The requirement is to create EC2 instance with ansible

Requirements:
- AWS Account
- Skill of Ansible to develop playbook
- Ansible installed in a controller node

Tasks:
- Create an EC2 instance or configure the machine in virtual box to consider it as controller node
- Install ansible-core with below command:
sudo dnf install ansible-core -y
- Configure the ansible.cfg file as per the requirement
- Login to AWS account and create an user with IAM:
- Assign policy "AmazonEC2FullAccess" to the userand create it.
- Once it is created, click on the user name of newly created user and click on security credentials
- Click on create access key and click on AWS Command line interface and click on next which will generate the AWS access key and the secret key which will be required to launch instance with ansible playbook.
- Go to ec2 dashboard and pick the following details:
   1. key_name i.e., SSH key to be used to connect the instance
   2. image i.e., the AMI image ID
   3. group i.e., the security group to be used
   4. instance_type (t2.micro for example)
   5. vpc_subnet_id (can be found in VPC section)
   6. aws_access_key (AWS access key created for the user for programatic access)
   7. aws_secret_key (AWS secret key created for the user for programatic access)
- Put all the these details in a yml file which can be used in vars_files to declare variable and to avoid displaying credentials in main code.
- Check the code : ec2.yml
- But while execution of the code, it will fail because no module of AWS is included in ansible-core, this need to be downloaded with ansible galaxy collection
- Install the collection with below command:
ansible-galaxy collection install amazon.aws
- Once it is installed, check the python version with below command:
python --version
- Now install boto3 and botocore as well:
pip3 install boto3 botocore
- Once the isntallation is successful, run the playbook and it will generate an ec2 instance 
