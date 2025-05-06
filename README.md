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
