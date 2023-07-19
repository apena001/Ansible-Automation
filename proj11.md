# PROJECT 11: Ansible – Automate Project 7 to 10

## INSTALL AND CONFIGURE ANSIBLE ON EC2 INSTANCE

### Update Name tag on your Jenkins EC2 Instance to Jenkins-Ansible. We will use this server to run playbooks.
### In your GitHub account create a new repository and name it ansible-config-mgt.
### Install Ansible

`sudo apt update`
`sudo apt install ansible`
`ansible --version`

![Alt text](<images/Screenshot 2023-07-15 101914.png>)

### Configure Jenkins build job to save your repository content every time you change it – this will solidify your Jenkins configuration skills acquired in Project 9.

- Create a new Freestyle project ansible in Jenkins and point it to your ‘ansible-config-mgt’ repository.
- Configure Webhook in GitHub and set webhook to trigger ansible build.
- Configure a Post-build job to save all (**) files, like you did it in Project 9.

### Test your setup by making some change in README.MD file in master branch and make sure that builds starts automatically and Jenkins saves the files (build artifacts) in following folder

ls /var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/

![Alt text](<images/Screenshot 2023-07-15 104548.png>)

![Alt text](<images/Screenshot 2023-07-15 110026.png>)

### Allocate Elastic IP to Jenkins-Ansible Server

## Step 2 – Prepare your development environment using Visual Studio Code

- configure VSC to connect to your newly created GitHub repository ansible-config-mgt.

![Alt text](<images/Screenshot 2023-07-15 114138.png>)

### Clone down your ansible-config-mgt repo to your Jenkins-Ansible instance

`git clone https://github.com/apena001/-ansible-config-mgt.git`

![Alt text](<images/Screenshot 2023-07-15 114103.png>)

### BEGIN ANSIBLE DEVELOPMENT

- In your ansible-config-mgt GitHub repository, create a new branch that will be used for development of a new feature.

- Checkout the newly created feature branch to your local machine and start building your code and directory structure

![Alt text](<images/Screenshot 2023-07-15 135958.png>)

- Create a directory and name it playbooks – it will be used to store all your playbook files.
- Create a directory and name it inventory – it will be used to keep your hosts organised.
- Within the playbooks folder, create your first playbook, and name it common.yml
- Within the inventory folder, create an inventory file (.yml) for each environment (Development, Staging Testing and Production) dev, staging, uat, and prod respectively.

![Alt text](<images/Screenshot 2023-07-15 141855.png>)

### Step 4 – Set up an Ansible Inventory

eval `ssh-agent -s`
`ssh-add /home/ubuntu/.ssh/id_rsa`

- Confirm the key has been added with the command below, you should see the name of your key

`ssh-add -l`

![Alt text](<images/Screenshot 2023-07-15 152121.png>)


![Alt text](<images/Screenshot 2023-07-15 152358.png>)

![Alt text](<images/Screenshot 2023-07-15 152951.png>)

### Now, ssh into your Jenkins-Ansible server using ssh-agent

![Alt text](<images/Screenshot 2023-07-15 153436.png>)

### Update your inventory/dev.yml file with this snippet of code:

![Alt text](<images/Screenshot 2023-07-15 154710.png>)

## CREATE A COMMON PLAYBOOK

### Update your playbooks/common.yml file with following code:

![Alt text](<images/Screenshot 2023-07-15 182656.png>)

### above command install wireshark utility

## Step 6 – Update GIT with the latest code

## RUN FIRST ANSIBLE TEST

`cd ansible-config-mgt`

`ansible-playbook -i inventory/dev.yml playbooks/common.yml`

![Alt text](<images/Screenshot 2023-07-19 153738.png>)

![Alt text](<images/Screenshot 2023-07-19 153427.png>)

`wireshark --version`

![Alt text](<images/Screenshot 2023-07-19 154016.png>)

![Alt text](<images/Screenshot 2023-07-19 155004.png>)

Thank you!!!