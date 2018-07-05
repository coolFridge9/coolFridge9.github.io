---
layout: post
title: Running a web app on an ec2
---
<img src="{{ site.baseurl }}/images/ec2.png" alt="Drawing" style="width: 300px;"/>
## What is an EC2?
It stands for Elastic Compute Cloud.  Its a virtual computing environment where you can continuosly open instances 
in the cloud with various operating systems.

You can use these instances to run a web application.

## Running at dotnet application on an EC2
I used an Ubuntu EC2 to run mine.
You need to install dotnet to run a dotnet application.

You can register the microsoft key with the following line:  
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb  
You install the required dependancies with:  
sudo dpkg -i packages-microsoft-prod.deb
(dpkg is packet managment software for installing)

The following 3 lines install dotnet 2.1:
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-2.1


The next step is to publish your application.  I did this by publishing on the rider editor.

You don't need to do this but I combined the publish folder into a .tar file using:  
tar -cvf publish.tar publish
(cvf = create verbose file)

I copied the .tar file to the ec2 with the following instruction:
scp -i "KeyPair.pem" /fileLocation/publish.tar ubuntu@ec2-num.ap-
southeast-2.compute.amazonaws.com:

the publish.tar file should now be on your ec2 so it needs to be uncompressed
tar -xvf publish.tar
(xvf = extract verbose file)

next you need to run the .dll file in the publish folder with:
dotnet project.dll

If you are not using a server, you can redirect traffic outside of your local machine using:
dotnet project.dll --urls http://ec2-num.ap-southeast-2.compute.amazonaws.com:5000

## Automatically booting up the app on start up
you need to put the app's publish folder in the root (to be accessed before the user loggin)  
Sudo cp -r publish /apps
I created a folder in the root called apps.

The next step is to to go to the file:  /etc/rc.local
and add the script to run the app at the bottom of the file eg:  
dotnet /apps/publish/GreetingWebsiteV2.dll --urls http://ec2-52-64-221-91.ap-southeast-2.compute.amazonaws.com:5000
