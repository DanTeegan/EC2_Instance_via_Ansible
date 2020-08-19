# Creating an EC2 Instance via Ansible

##### 1) First, spin up a Virtual Machine. I have created a VM called Ansible in this demonstration.

##### 2) Then ssh inside the virtual machine previously created. ``` vagrant ssh ansible ```

##### 3) Once inside go ahead and install all Pre-requisites needed for Ansible. The commands can be seen below:

```
sudo apt update

sudo apt install software-properties-common

sudo apt-add-repository --yes --update ppa:ansible/ansible

sudo apt install ansible
```
##### You can also install tree to present the files in more aesthetically pleasing manner
```
sudo apt-get install tree
``` 

##### 4) Once ansible in installed we can now start downloading the EC2 module dependencies. They can be seen below:
```
sudo apt install python

sudo apt install python-pip -y

sudo pip install --upgrade pip

sudo pip install boto

sudo pip install boto3
```
##### 5) Once all dependencies are installed we can now move on to the SSH key creation.

```
ssh-keygen -t rsa -b 4096 -f ~/.ssh/<Your_Name>_aws
```

##### 6) Now we can create the Ansible directory structure. The code for this can be seen below:
```
mkdir -p AWS_Ansible/group_vars/all/
cd AWS_Ansible
touch playbook.yml
```

##### 7) Now we can edit the vault and store the EC2 secret and access keys
```
ansible-vault edit group_vars/all/pass.yml
```
##### You will be prompted to enter a pass phrase 

##### 8) Once inside you will need to click ```i``` in order to insert and then paste in the following code
```
ec2_access_key: <Your_Access_Key>                                     
ec2_secret_key: <Your_Secret_Key>
```
