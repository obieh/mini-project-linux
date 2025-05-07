# mini-project-linux
## This project demonstrates how to create an Elastic Compute Cloud (EC2) instance.

* ### Go to [aws website](https://signin.aws.amazon.com/signup?request_type=register) and create an account if not already.
* Login to the account you just created
* On the search bar, tpye **EC2** and click on th first option **EC2 Virtual Servers in the Cloud**
![searc](./img/search-ec2-.png)

* On the next page click *Launch instance* 
![launch](./img/launch-instance.png)

## Filling out EC2 instance details
* Fill the name of your server
* Select ubuntu for OS image type
* Make sure it is _free tier eligible_
![fill](./img/fill-out-1.png) 

* Select instance type _t2 micro_ and confirm it is _free tier eligible_

![fill](./img/fill-out-2.png)

* Type your key-pair name, _RSA_ for key pair type and _.pem_ for key pair format and click **Create key pair**
![fill](/img/fill-out-3.png) 

### Key pair will automatically download to your local computer.

* Create a Secuirity groupm be sure to check _Allow ssh traffic_ and from any IP address

![fill](./img/fill-out-network-4.png)

* Next, Increase the storage size to 15gb, specify the number of instances you want to create

![fill](./img/fillout-storage--5.png)

* Click _Launch instance_ to create the Ec2 VM on AWS

![launch](./img/launch-6.png)

* You should see the VM building.
![launching](./img/instance-launching.png)

* Once ready, go to your dashboard to see the VMs running on your account.

![vms](./img/running.png)

## Connecting to the instance(ssh)
* Find the public IP address of the running instance

![ip](./img/ip-address.png)

### To connect to the VM click on _connect_ while the the name checkbox is checked.

![connect](./img/click-connect.png)

### Another window pops. Click **ssh client** tab to see how to connect to the instance, Copy the example given.

![ssh](./img/ssh-client.png)

### Head over to your terminal and change directory to the location of the .pem file downloaded earlier. In this case Downloads.

* `cd Downloads`

### Now paste the example command you copied from the ssh client tab and hit enter.

* `ssh -i "linux-mini-project.pem" ubuntu@ec2-3-129-73-101.us-east-2.compute.amazonaws.com`
![bad](./img/bad-permission.png)

### Connection was denied due to permissions issues on the .pem file as shown above.

*  Run `chmod 400 linux-mini-project.pem`

![chmod](./img/chmod.png)

### Try connecting to the instance again

![con](./img/connected1.png)

![con2](./img/connect2.png)

### Connection was successful as shown above.

## Package managers

### since our linux distrobution is Ubuntu A debian based. Adavnced Package Tool(apt) is the appropriate package manager

### Updating and installing softwares on the EC2 instance.

* Run `sudo apt update`

![update](./img/sudo-apt-update.png)

* Run `sudo apt install tree` to install tree on the VM.

![tree](./img/install%20tree.png)

### verify th installed package

![tree](./img/test-tree.png)

* Run `mkdir project` to create a folder namde project.

![folder](./img/mkdir.png)

### Install nginx

* Run `sudo apt install nginx` to install nginx webserver on the VM.

![nginx](./img/install-nginx.png)

#### Nginx might require you to start nginx

* Run `sudo systemctl start nginx` to start nginex service.

### Check if the nginx service is up and running

* Run `sudo systemctl status nginx` to check nginx status

![service](./img/nginx-status.png)

### Nginx service is running. Now copy your instance public ip address and head to your browser to confirm nginx service is available.

![bad](./img/web-ngnx-no-show.png)

### We could not access the service, we head aws account and check secuirity settings of the instance. 
### We had only allowed ssh connection to the machine.
![](./img/inbound-rule1.png)

### The inbound rule will have to edited to allow other traffic to rech the machine. Click _edith inbound rules_ in the secuiity group
![](./img/edit-inbound-1.png)

### Click add rules and allow all trafic from all sources then save. Please note that allowing all traffics is not advised on production enviroment. Allowing all traffice is only for the purposse of this project or for development enviroment only.

![](./img/save-inbound-rule.png)

### Verify the inbound rules you just edited have been saved

![](./img/afta-edit-save-inbound.png)

### Head back to your browser and refresh

![](./img/welcome-nginx.png)

### We can now see the nginx welcome page to prove that nginx service is publicly available.