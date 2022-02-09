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
Voila! alas you have successfully deployed your first VM in the Azure portal. Now you can view your newly created Azure VM by clicking "Go to resources at the bottom-left of your screen.


![](./images/deploymentcompleteimage.png) 





