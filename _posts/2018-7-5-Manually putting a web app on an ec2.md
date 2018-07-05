---
layout: post
title: Running a web app on an ec2
---

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

The following 3 lines install dotnet 2.1:
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-2.1


The next step is to publish your application.  I did this by publishing on the rider editor.

You don't need to do this but I combined the publish folder into a .tar file using:  
tar -cvf publish.tar publish

I copied the .tar file to the ec2 with the following instruction:
scp -i "KeyPair.pem" /fileLocation/publish.tar ubuntu@ec2-num.ap-
southeast-2.compute.amazonaws.com:

the publish.tar file should now be on your ec2 so it needs to be uncompressed
tar -xvf publish.tar

next you need to run the .dll file in the publish folder with:
dotnet project.dll

If you are not using a server, you can redirect traffic outside of your local machine using:
dotnet project.dll --urls http://ec2-num.ap-southeast-2.compute.amazonaws.com:5000
