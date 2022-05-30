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
- Notice that vmA can access vmB's private IP address because of the default rule of allowing connections within a virtual network

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171046225-454195c8-3ed3-45c0-a807-26c43392007d.png" height="50%" width="50%" alt="UDR"/>

<p/>

# Create a Route Table
- Add a route
- Address prefix: 10.0.0.0/16 is the address space of the Vnet. Any traffic within the vnet will route to the next hop address which is the private IP of centralvm
- We want centralvm to be the virtual appliance that captures all traffic first

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171048793-1afb8931-46ee-47df-8988-dc6439ccb6d7.png" height="90%" width="90%" alt="UDR"/>

<p/>

# Associate the route table with the subnets, this is the step where it will be effective
- Associate subnet A with this route table created.
- Now, all traffic from subnet A will flow towards the centralvm virtual appliance first 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171048971-1bbc5770-01ab-44bb-ad81-91f8c0dcb853.png" height="90%" width="90%" alt="UDR"/>

<p/>
- Result after associating subnet A to the custom route table
- This occurs because it reaches the central VM and not subnetB

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171049259-5b7da9f0-6064-4091-aa3a-8a2107586c32.png" height="90%" width="90%" alt="UDR"/>

<p/>

- We must enable forwarding on the centralVm's NIC
- Now, when a request is being made from the VM in subnetA for the vmB in subnetB, centralvm forwards the request it to the vmB within subnetB

# However, we must also configure forwarding request at the OS layer on centralVM
- Install Remote Access > Routing > DirectAccess and VPN (RAS)

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171050155-d7b997ef-91ad-4c30-8698-dc48199e362e.png" height="90%" width="90%" alt="UDR"/>

<p/>


# After downloading and installing the role 
- Open the getting starting wizard on the right corner
- DeplyVPNonly > Right click on centralvm and select configure and enable routing and remote access > custom configuration > LAN routing > finish and start service
- Refresh the page and see that the forwarding requests is enabled

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171059360-afc79af0-55b9-4abd-b26d-e535e92cb7c3.png" height="90%" width="90%" alt="UDR"/>

<p/>


<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/171060788-b26c8e04-4874-4afc-b44e-569804f1ac15.png" height="90%" width="90%" alt="UDR"/>

<p/>

