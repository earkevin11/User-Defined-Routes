# User-Defined-Routes

# What are user-defined routes?
- When users want to define custom routes within a Virtual Network, use UDR when admins want to route traffic a particular way



# Use Case
- Create a virtual network with 3 virtual machines in their own subnets
- Route traffic going to vmA and vmB to the central subnet first.

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170851773-e7af33b2-080c-4339-9828-7099b9f2cef8.png" height="75%" width="75%" alt="UDR"/>

<p/>

# Create three subnets and ensure each virtual machine has their own subnet
- Notice that there are three subnets:
- Central Subnet
- Subnet A
- Subnet B

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171035918-b78b63f9-95bd-4238-a614-82dd84f63467.png" height="255%" width="255%" alt="UDR"/>

<p/>

# Create the two vms and ensure each one is in SubnetA and Subnet B

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171037253-57d23da8-0c36-43ce-b880-90cc241b17bb.png" height="50%" width="50%" alt="UDR"/>

<p/>

- For vmB, open port HTTP 80 and RDP so admins can access IIS

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171040735-e184f7d3-db56-4a74-837d-8e22c7447e34.png" height="50%" width="50%" alt="UDR"/>

<p/>

# For vmB: download IIS Web Server and create an HTML page and save it within wwwroot
- Access vmB IIS within vmA
- Notice that vmA can access vmB because of the default rule of allowing connections within a virtual network

<p align="center">
  
<img src="" height="90%" width="90%" alt="UDR"/>

<p/>



<p align="center">
  
<img src="" height="90%" width="90%" alt="UDR"/>

<p/>



<p align="center">
  
<img src="" height="90%" width="90%" alt="UDR"/>

<p/>
