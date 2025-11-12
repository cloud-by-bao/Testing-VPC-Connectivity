<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Testing VPC Connectivity

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-connectivity)

**Author:** Bao Luong  
**Email:** baodevops21@gmail.com

---

## Testing VPC Connectivity

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-connectivity_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a private, isolated network within the AWS cloud, allowing you to launch AWS resources in a virtual network that you control. It is useful because it offers enhanced security, customizable networking, and granular control over your network environment, mirroring a traditional data center's network while leveraging the scalability of the AWS infrastructure

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to test EC2 connectivity with ping:  I made sure that the public and private servers can communicate with each other using the ping command. Also, I had to update your Private Server's NACL settings to make this work.
FInally I had to verify VPC internet access with curl: command.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was to that I can SSH into an EC2 by using EC2 connect.

EC2 Instance Connect is an alternative way to use SSH - Instance Connect lets you securely connect to your EC2 instances directly using the AWS Management Console. You're still using SSH, but with all the key management handling it for you. This takes away a lot of the complexity of setting up SSH.

### This project took me...

This project took me an hour

---

## Connecting to an EC2 Instance

Connectivity means it is all about how well different parts of your network talk to each other and with external networks. It's essential because connectivity is how data flows smoothly across your network, powering everything from simple web hosting on the Internet to complex operations.

My first connectivity test was whether I could connect to EC2 instance called Public Server.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-connectivity_88727bef)

---

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is an alternative way to use SSH - Instance Connect lets you securely connect to your EC2 instances directly using the AWS Management Console. You're still using SSH, but with all the key management handling it for you. This takes away a lot of the complexity of setting up SSH.

My first attempt at getting direct access to my public server resulted in an error, because the inbound rules in the security groups did not include SSH yet.

I fixed this error by adding the SSH inbound rules in the security groups.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-connectivity_1cbb1b88)

---

## Connectivity Between Servers

Ping is a common computer network tool used to check whether your computer can communicate with another computer or device on a network.

 I used ping to test the connectivity between my Public Server to the Private Server. 

The ping command I ran was ping 10.0.1.227

The first ping returned nothing, This meant that it is not recieving a respone from the other server.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-connectivity_defghijk)

---

## Troubleshooting Connectivity

I troubleshooted this by adding the All ICMP - IPv4 in the inbound rules for both the Private NACL and securty groups settings.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-connectivity_4a9e8014)

---

## Connectivity to the Internet

Curl is a tool to test connectivity in a network. That means on top of checking connectivity, you can use curl to grab data from, or upload data into other servers on the internet!

I used curl to test the connectivity between the Public server and example.com.

### Ping vs Curl

Ping and curl are different because ping checks if one computer can contact another (and how long messages take to travel back and forwth), and curl is used to transfer data to or from a server.

---

## Connectivity to the Internet

I ran the curl command curl https://learn.nextwork.org/projects/aws-host-a-website-on-s3 which returned complete HTML content of NextWork's web app (specifically, the first project on the web app), which is why you now see a large amount of HTML data.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-connectivity_8ee57662)

---

---
