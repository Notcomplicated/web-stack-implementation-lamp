# web-stack-implementation

Howdy ya'll and welcome to my first Web Stack Implementation project!

What is a Web Stack? It is is a group of software components, used to implement or set up various applications (for example, a website). The "stack" refers to the specific layered components (e.g. OS system, webserver, script interpreter, and database) which are built on top of each other. One of the most popular web stacks include LAMP, which stands for Linux, Apache, MySQL, and PHP or Python or Perl. The LAMP stack will be used for this project!

# LINUX

## Setting up your virtual environment

Linux is an operating system (OS) just like Windows, iOS, and Android. It is the best known and most used open source operating system in the world. It is flexible and easy to configure.

In order to complete this project, it is necessary to set up a virtual environment. In order to achieve this, first, create a free [Azure account](https://azure.microsoft.com/en-us/features/azure-portal/) and then create a virtual machine (VM) using the Ubuntu Server OS. More details in the following section!

You may be wondering, 'what is Azure'? Azures is a cloud service provided by Microsoft. One the leading Cloud Service Providers in the world. Azure offers a wide variety of databases and services for different types of applications. This allows users to choose the right tool for the job while receiving the best cost and performance.

Azure offers a Free Trial for newly registered account users. This enables users to try out some Azure services free of charge over certain period. For this project, we will utilize the [Azure VM](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/overview) service, which is covered by the Free Trial version!

**Let's get started!**

Begin by registering and setting up an [Azure account](https://azure.microsoft.com/en-us/features/azure-portal/) and following the directions on the screen. Once you have created your AWS account, navigate to the login page and type in your credentials.

![](./images/image1.png)

Once you've signed into the Azure portal, we would need to creat and provision a new VM. There are a few ways to go about it. you can use the create a resource (plus sign) or, finding the Virtual using Quick search or clicking home and finding the virtual machine blade. 

![](./images/image2.png)
In this instance I will click Virtual machines directly from the Azure services page. 

This will take me to the next page to create a new VM. Here, I will click create and select Virtual machine from the dropdown options.

![](./images/image3.png)

This will take me to the next page where I will need to fill out informations pertaining to the VM I intend to create. 
For the subscription page I will leave it as the default Azure subsription. 
For resource group I will create a new one and name it webstackimplementationproject1
I will name my VM project1VM
For region, I will choose the closest region to me which in this case will be US west
I chose Ubuntu Server 20.04 LTS since that is what we plan on running for this project.
I will leave the size as the defualt and SSH public key.


![](./images/image4.png)

I will leave the username as the defualt, in this case which azureuser
I will choose Generate new key pair for the SSH public key source
My key pair name will be filled as project1VM_key
Select Allow selected ports for the public inbound ports
Make sure select inbound ports is SSH 22.

![](./images/image5.png)

Now clicking next will take me the to the Disks page. Since I will not be making any changes in this esction, I will leave all the options to the default.

![](./images/diskspageimage.png)


Now I will click next which will take me to the networking page. Again I will not be making any changes here, therefore all selections will be left as the defualt. 


![](./images/networkingpageimage1.png)

![](./images/networkingpageimage2.png)


Next we move the management page but here also I will leave all the defaults selected. 

![](./images/managementpageimage1.png)

![](./images/managementpageimage2.png)


Because I have no need to make any changes in the Adanced and Tags sections, I will proceed to click the review and create button.  This will take me the review + create page after it has gone through validation and passed. On here we see the products details of the VM we intend to create. Also on this page is the Terms and all the choices selected to create the VM.


![](./images/reviewcreatepageimage1.png)

![](./images/reviewcreatepageimage2.png)

![](./images/reviewcreatepageimage3.png)

![](./images/reviewcreatepageimage4.png)



After reviewing and making sure everything is how you want it, You will  proceed to click the create button which will begin the proviosioning of the VM.  
Before the VM completes deploying, a generate new key pair window will pop up which you will select Generate and create new key pair. 


![](./images/generatenewkeypairimage.png)


A different window will pop asking us to save the generated new key in a .pem file. You will click ok the save the newly generated key pair for use later in this project. 


![](./images/keypemimage.png)


Finally, you will see a notification telling you the deployment of your VM is complete. 


![](./images/deploymentcompleteimage.png) 

Voila!! alas you have successfully deployed your first VM in the Azure portal. Now you can view your newly created Azure VM by clicking "Go to resources at the bottom-left of your screen.




# Connecting to your VM from your local PC

**PLEASE NOTE** - Anchor tags < > will be used to indicate contents what must be replaced with your unique values. For example, if you have a file named "**keypair123.pem**" you must enter this information within the corresponding anchor tag: < **private-key-name**>

Now let's connect to our VM!

Begin by opening Terminal. Once you have opened Terminal, use the ==cd== command to change into the directory that your key pair is located. This is usually the ~/Downloads directory. If you are having difficulty finding it, you can use the ls command to list the contents of your current directory.

Once you have located the key pair, use the command below to activate the key file (.pem). This command will also change permissions (otherwise you may get the error “Bad Permissions”):

$ sudo chmod 0400 <private-key-name>.pem

When prompted, type the password for your local PC and press Enter on your keyboard.

Next, go back to the Azure console for a moment, and navigate to your running VM . Copy the Public IP address . 

Now that you've copied the Public IP address, go back to Terminal. Connect to the EC2 VM by using the command below:

$ ssh -i <private-key-name>.pem ubuntu@<Public-IP-address>

Next, you will be asked if you want to continue connecting. Type Yes and press Enter on your keyboard.


![](./images/sshimage2.png)


Nice job! You have successfully connected to your Linux server in the Cloud environment.



# APACHE

**Installing Apache on the virtual environment**

What is Apache? Apache is a widely-used fast, reliable, and secure web server software. A web server acts as a middleman between the website visitor browser and the server.

Now we will install Apache using Ubuntu’s package manager: [‘apt’](https://guide.ubuntu-fr.org/server/apt.html) . Begin by using the $ sudo apt update command to check for any available updates.

Next, run the following command to run the Apache package installation:

$ sudo apt install apache2

Terminal will generate a series of code. 

Once completed, use the following command to verify that Apache2 is running as a servive in our OS:

$ sudo systemctl status apache2

If there is a green dot, then it means it's running just how you want and it should look like the image below:


![](./images/apache2greendotimage.png)


# Modifying The Firewall

In order to receive traffic to our Web Server, it is imperative to open TCP port 80. This is the default port that web browsers utilize in order to access web pages on the Internet.

When we created the VM on the Azure console,the TCP port 22 was opened by default. This allowed us to access the VM via SSH in Terminal. However, we must add a rule to the security groups of our VM configuration, in order to allow inbound connections through port 80.

Begin by navigating to the networking tab for the newly created VM. Click on "Add inbound port rule to tab to your right and edit the inbound port rule for port 80 .


![](./images/addinboundportruleimage.png)


Under the service, choose HTTP in the dropdown menu and the click add at the bottom left. 


![](./images/port80image.png)



Now let's verify whether or not we can receive traffic. On the Terminal, use the command to send a request the Apache HTTP Server on port 80.

$ curl http://localhost:80

You should see something like this:


![](./images/portaccessimage.png)


Next, let's try to verify access through the web browser using the public IP address of the VM. Open a web browser of your choice and then enter the following url (remember to replace contents within the **Anchor Tabs** < >):

http://<Public-IP-Address>:80

You should see the following web page. This is Apache2 Ubuntu Defualt page:


![](./images/apache2defaultimage.png)




