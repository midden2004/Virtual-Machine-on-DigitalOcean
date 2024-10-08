# Virtual-Machine-on-DigitalOcean
## What is DigitalOcean?

DigitalOcean is a cloud computing platform that provides developers and businesses with scalable and flexible infrastructure for building and deploying applications. It was founded in 2011 and is headquartered in New York City.

DigitalOcean offers various services, including virtual private servers (VPS), load balancers, object storage, and managed databases. The platform is designed to be simple and easy to use, with an intuitive user interface and API that allows developers to spin up and manage their infrastructure easily.

One of the critical features of DigitalOcean is its focus on providing affordable and predictable pricing, with plans starting at just $5 per month. This makes it an attractive option for startups and small businesses that need to keep costs low while still having access to robust infrastructure.

For GitHub Student Developer Pack, GigitalOcean gives $50 free credits to the new user.

### 1- Register and create a VM instance:

#### Droplet (Virtual Machine):

To create a Droplet which is known as a virtual Machine on DigitalOcean. we need to select the project first and then click on “Spin up a Droplet”. We can rename the droplet. And then we have to select the following options

#### Region: 
Choose a region that is near according to your Geo location.

#### OS image:
Ubuntu(version: 22.10 x 64). You can select any other image according to your need.

#### Droplet: 
Basic(this is recommended for student Package)

#### CPU: 
Premium Intel with $56/month and 8GB/ 4 Intel CPUs. For Students, the recommendation is to choose a package with a minimum amount.

### 2- Configure SSH keys for secure access to the VM:

#### SSH Key:

And then add a new SSH key. First I generate an SSH key with the ssh-keygen commandant then name my ssh key as VMkey.

This command generates two keys one is the public (VMkey.pub)and the other is the private key(VMkey). Which I stored to get access to Droplet.

And then paste the key.pub in the SSH content and the name is VMkey. And new key is Added to the cloud.

I choose One VM only. And after creating the droplet. A new droplet is added to the account.

### 3- Access the VM using SSH

To access the Virtual Machine on my local terminal I use this command

    ssh -i ./VMkey root@139.59.73.27
where 139.59.73.27 is the IP address of the droplet and ./Vmkey is the private key. This Command Give Access to the Virtual Machine.

With “free -h”, We can get Stats of our Virtual Machine.

### 4- Add custom firewall rules in the subnet’s security list:

To add a new Firewall. We need to select the networking option given at the side and then we need to select Firewalls and then click Create Firewall. we need to select inBounds and outBounds to secure our droplet. If we want to secure the droplet then we should be allowed specific IPs rather than select ipv4 and ipv6.

Here is how I select inbound and outbound Rules.

<img width="558" alt="image" src="https://user-images.githubusercontent.com/74543712/219961953-8d48061d-7f88-4dea-bdec-6d7f4e23c392.png">

<img width="540" alt="image" src="https://user-images.githubusercontent.com/74543712/219961964-82fa58cd-45ab-491b-bbe7-b9d6fb15c155.png">


This is not very Secured because any IP can get access with HTTP, HTTP, and SSH requests. that’s why it's recommended to all enter the IPs which are authentic and authorized.

#### Testing:

For testing purposes, I just remove ssh’s sources from inbound and then I am not able to connect with my VM. Because I don’t have access to it.


### 5- Installing RDP in VM and accessing the VM using RDP from your PC:

Now I turned off the VM and select Boot from Recovery from ISO and then launch the recovery Console and Write the following command:

    wget -O- https://ia801501.us.archive.org/26/items/windows-10byronit/Windows10byronit.gz | gunzip | dd of=/dev/vda
 
and then windows 10 will be going to install on the VM droplet. It will take some Time.

After installation. We need to off the VM and then select Boot from the hard drive and then Enter the console. And now I got access to windows 10 on the console.


After installation, We need to do IP configuration to access this virtual Machine on a Local PC.

<img width="596" alt="image" src="https://user-images.githubusercontent.com/74543712/219962057-73378a50-98f4-49de-bd17-ab7a4dff9d52.png">

Administrator
Noob@12345678

Now we will configure the network settings of the server. Click on the network icon at the bottom right of the screen. Then click the “Network & Internet settings” button.


Then click on the “Ethernet” tab.


Click on “Change adapter options”.


Right-click on an adapter and click “Properties”.


Double-click on “Internet Protocol Version 4 (TCP/IPv4)”.


We fill in the IP addresses using the information written at the bottom of the screen. Enter the DNS addresses 1.1.1.1 and 8.8.8.8 and click the “OK” button.


We are now connected to the internet.


Now we will make the necessary settings to make a remote desktop. At the start, we will write “remote desktop settings”. It’s okay if no Turkish characters appear; type “remote table,” and you will see it in the results.


We click on the switch that says “Off” to enable remote desktop. We continue the warning by saying, “Confirm”.


Click on “Advanced settings” from the same screen.


We’re removing the box in front of “Computers require Network Level Authentication to connect (recommended)”. We continue the warning by saying, “Proceed anyway”.


Now we can connect to the server with Microsoft’s own remote desktop software.

### Conclusion:

In this article, we Learn how to create a Virtual Machine and create windows 10 instances on that, which will be accessible on Local Machine. It is recommended to create Firewall and allow only specific IPs to get access to the Virtual Machine and don’t share your ssh private key with anyone else.






