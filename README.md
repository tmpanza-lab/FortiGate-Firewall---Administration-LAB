# FortiGate Firewall - Administration LAB

## Objective

The FortiGate Firewall - Administration Lab project is aimed to provide hands-on experience with configuring, managing, and maintaining a FortiGate firewall. Each section introduces a critical component of FortiGate administration, helping IT security professionals to gain practical knowledge and skills in key areas of firewall setup, monitoring, and management.

### Skills Learned

- Basic FortiGate Administration Skill
- Network Configuration and Management 
- Security Management Skills
- Backup and Recovery 
- Firmware and Feature Management
- Monitoring and Alerts
- Performance Optimization
- Policy Management


### Tools Used

- FortiGate VM: A virtual appliance used in virtualized environments, such as VMware or Hyper-V
- FortiOS Web Interface (GUI)
- FortiOS Command Line Interface (CLI)
- FortiView Dashboard: Built-in monitoring tool for real-time traffic and event analysis.
- Backup and Restore Tools
- FTP/HTTP/HTTPS Servers: For uploading firmware or serving configurations during the lab.
- Traffic Generation Tools
- GNS3 for simulated network devices (e.g., routers, PCs, or switches) to test


*Ref 1: Network Diagram*
![image](https://github.com/user-attachments/assets/c325ea04-f529-4443-b767-35c4e628bd9d)

 

## Steps

## Fortigate Initial Setup

## Fortigate Access ##

We have 3 options to connect to our FortiGate unite:

1) Via Web 

2) Via CLI (SSH)

3) Via console

The appliance come from the factory with the port1 already configured with the IP@ "192.168.1.99"

# LOGIN

the login is "admin" for user and the password is empty  

# Change Hostname 

FortiGate-VM64-KVM # config system global 

FortiGate-VM64-KVM (global) # set hostname FGT1

FortiGate-VM64-KVM (global) # end
![image](https://github.com/user-attachments/assets/17807e80-3e43-4b64-ae9c-cb00b9f9ca4c)

 

# Interfaces Configuration

FGT1 # config system interface 

FGT1 (interface) # edit port1 

FGT1 (port1) # set mode static 

FGT1 (port1) # set ip 192.168.1.99/24

FGT1 (port1) # set allowaccess http ping ssh

FGT1 (port1) # set alias LAN1

FGT1 (port1) # set role lan 

FGT1 (port1) # end
![image](https://github.com/user-attachments/assets/29b81cac-95f5-4abe-a895-b2bdcc417975)
![image](https://github.com/user-attachments/assets/190524af-ddfc-4c95-93b5-b278e80d11e2)
![image](https://github.com/user-attachments/assets/9b6080b1-44b7-4fb2-a96b-4a3c0492d535)
![image](https://github.com/user-attachments/assets/1580cb33-b431-4c02-b44d-06891dbefa87)
 
 
 
 

### Ping From Cli ###
![image](https://github.com/user-attachments/assets/ebf976a6-1c85-409c-856f-06682296e53c)

 

# execute ping
![image](https://github.com/user-attachments/assets/97f7fcb0-15a8-497a-905c-ddc50378e422)
 





This is our Dashboard
![image](https://github.com/user-attachments/assets/5fba265d-c497-49da-b383-6f005349149d)
 
Settings
![image](https://github.com/user-attachments/assets/b8a47cea-1bd5-4ef5-b569-db7ed69688cd)

 
Network Interfaces
![image](https://github.com/user-attachments/assets/dd0e0778-2137-4b56-aacb-b3d7e74e3941)
 

Port 1 Configuration we did in CLI.
![image](https://github.com/user-attachments/assets/d5471543-7b68-46d4-b344-0aa092964b3b)
 







# Admin Users
![image](https://github.com/user-attachments/assets/a3e45a52-abdc-4acf-a8d4-5b43b1fdf5f3)
![image](https://github.com/user-attachments/assets/857af04b-2d6f-4f0d-851b-60337816fba0)
 
 
User created
![image](https://github.com/user-attachments/assets/b5333615-a4cf-4b2b-a081-d357f4ba4a98)
 
Test User access
![image](https://github.com/user-attachments/assets/80533c78-a08c-4ae0-ad71-5d4855e02a05)
 
Access permissions
![image](https://github.com/user-attachments/assets/38980a07-8904-4f74-88ea-354d75ec93cc)
 
Prof Admin is a custom profile
![image](https://github.com/user-attachments/assets/34683499-6a89-4d58-a789-ccd48ce327ee)
 

Customized Read access for Security 
![image](https://github.com/user-attachments/assets/a1d0d476-2e51-4205-b904-12e6f83d0999)

 

For example, if we want a user to only have read access to security fabric Menu and also have ready access to only network.
I will create a new admin user I will name it test I'll create a password for it.
I need to choose the administrator profile I will choose the profile and I will try to log in with it.
![image](https://github.com/user-attachments/assets/da1e7bc2-b259-469e-919e-0da66506b871)
![image](https://github.com/user-attachments/assets/450f797c-e470-40a9-b61d-fdd38fceff56)
![image](https://github.com/user-attachments/assets/776c7d27-7816-42b2-8954-835dd59d7c1a)
![image](https://github.com/user-attachments/assets/aedbc1c8-bfdb-490f-a8ab-82fc52a1b62c)
 
 
 
 

## Create Admin Users From CLI ##


FGT # config system admin

FGT (admin) # edit user
new entry 'user' added

FGT (user) # set vdom root

FGT (user) # set password superpassword

FGT (user) # set accprofile super_admin

FGT (user) # end

FGT #
![image](https://github.com/user-attachments/assets/a3135c8b-5dde-4a2d-a0bb-85b2c292560a)
![image](https://github.com/user-attachments/assets/391eaf30-cbcd-4866-809b-fd40df3c31c6)
![image](https://github.com/user-attachments/assets/68bb115a-a769-4831-a01e-ae84e245fa03)
![image](https://github.com/user-attachments/assets/eec438c3-d2f6-4a30-a71c-0bbedacb45a3)
 
 
 
 

# Secure Access

As an admin, one of your responsibilities is to secure access to your FortiGate firewall. And one of the things that we can do to secure our FortiGate Firewall access is to set up a strong password and to restrict access to only trusted devices.
 ![image](https://github.com/user-attachments/assets/62c22688-e46e-40f6-9af5-182c0ff0e31d)
![image](https://github.com/user-attachments/assets/65020452-b142-4397-9354-753ecf75f0ab)


 

Apply Policy Settings to Admin
![image](https://github.com/user-attachments/assets/f9d96453-8f8f-432e-9115-383d1059854b)
![image](https://github.com/user-attachments/assets/68718a92-1518-4e95-bc85-24bb41d77b63)
 
 


## Reset Admin Password ##

In case of lost or forgot of admin password we need to reset it
To reset it we need to have physical access to the unit.

We will need:

- Console Cable 

- Access Programe (Putty...)

- Fortigate Serial Number

1) Reboot fortigate

2) in the username field type the user "maintainer"

3) in the password field type bcpb + Servial Number (bcpbSERIAL NUMBER)

then:

FGT1 # config system admin 

FGT1 (admin) # edit admin 

FGT1 (admin) # set password newpassword

FGT1 (admin) # end
![image](https://github.com/user-attachments/assets/9832477e-5f80-4a93-996c-86a832c3181a)





# Interface Configuration # 
![image](https://github.com/user-attachments/assets/b8b175df-291a-4987-a96b-f06a7fe1fffe)

 

config system interface

edit port3

set mode dhcp

set allowaccess http ping ssh

end

get system interfaces physical 
![image](https://github.com/user-attachments/assets/76ff6081-207a-45f3-9d2b-a14adc28d7ee)
![image](https://github.com/user-attachments/assets/0e20305c-ccdc-43e3-bc14-1bfc746539b0)
![image](https://github.com/user-attachments/assets/8a6c4808-4da8-412d-8511-5829f38556fd)
![image](https://github.com/user-attachments/assets/9938dc0c-d3c7-47f0-bb51-3861e7d12039)
![image](https://github.com/user-attachments/assets/38ef1e38-7286-4f0d-bd1f-f96ed7d2a4a7)
 
 
 
 
 

# CLI BACKUP # 

execute backup config tftp FGT-V1 192.168.243.2
![image](https://github.com/user-attachments/assets/553ac369-aa69-4ec4-b48a-b83539bb699e)
 
This is our backup file
![image](https://github.com/user-attachments/assets/15b7d041-8b71-4b3e-a808-dc93f489f4c1)
![image](https://github.com/user-attachments/assets/c190f955-97d1-41d0-86de-42e515d0c1c0)
 
 


## TFTPD64 DOWNLOAD LINK ##

https://bitbucket.org/phjounin/tftpd64/downloads/


# Firmware Upgrade
![image](https://github.com/user-attachments/assets/902cd34a-6637-45bc-b237-9d4628ef8f8b)
 

Go to Fortinet Support Website https://support.fortinet.com/welcome/#/
![image](https://github.com/user-attachments/assets/d414fc52-b6a4-4bea-b43e-9984e4a0fcd4)


 
Create and account and login
![image](https://github.com/user-attachments/assets/39198d91-f000-418a-8c51-0e0cd16b14d1)
![image](https://github.com/user-attachments/assets/87a144e7-931e-4bc2-9fcf-1de1b9769459)
![image](https://github.com/user-attachments/assets/d2f48ae6-7775-420e-9904-8202804a6012)
 

 

 
Click Download
![image](https://github.com/user-attachments/assets/f9a2502e-d658-4cf6-a892-ef9e9db34234)
 



## Addresses Object

### Addresses Creation ###
![image](https://github.com/user-attachments/assets/1c9447c5-055a-47d7-93ed-f0cbe1c4136f)
 
Types
![image](https://github.com/user-attachments/assets/dca4c3d3-e381-407d-8b05-7efcd3355379)
![image](https://github.com/user-attachments/assets/4fd565ad-df7b-4041-8783-9e3f80e4f716)
 
 
My address object is created now
![image](https://github.com/user-attachments/assets/2bac103b-b76a-49e2-84a9-db14c69cfd27)
 
Firewall Policy
![image](https://github.com/user-attachments/assets/1db5fe0c-c307-4858-ab81-8b59b27fef63)
 
Select DMZ that we created and click OK
![image](https://github.com/user-attachments/assets/a62cd448-7480-4eba-8d3f-10ef52405d21)
![image](https://github.com/user-attachments/assets/7fc57a20-ebd7-4b4c-8218-507101f3cf6f)
 
 

Create another for IP Ranges
![image](https://github.com/user-attachments/assets/139f133b-7c21-44c4-9dbd-500e8d41b616)
 
We can now change the Firewall Policy to IP Ranges
![image](https://github.com/user-attachments/assets/f81418e6-f460-4e9d-8851-6d00195146cb)
 

Create another for a single host IP
![image](https://github.com/user-attachments/assets/1716b559-60c9-4847-bb57-7faac5836847)
 
Block / Allow certain regions
![image](https://github.com/user-attachments/assets/41f46996-7ad9-4b6f-85f7-1a63161fbf46)
 


# Subnet configured through CLI and IP range
![image](https://github.com/user-attachments/assets/1fac4992-5684-475b-8169-3ca1b782da8b)

![image](https://github.com/user-attachments/assets/b3845c11-1edd-479e-a8e5-9fc1e347a983)
 
 

DHCP-CONFIGURATION
![image](https://github.com/user-attachments/assets/1cbbdfbe-914c-4525-9628-7581e4b1d8cc)
![image](https://github.com/user-attachments/assets/9d51ba83-e0ab-4fca-8992-2930444528fd)
![image](https://github.com/user-attachments/assets/db1ce402-24cc-49a8-8bfd-6e38d74f22de)

 
 
 

Set Webterm client to use DHCP
![image](https://github.com/user-attachments/assets/2fb17a9f-e43d-4890-a08b-e6b89757eb66)
![image](https://github.com/user-attachments/assets/2e64445b-9117-4e18-adc1-dfe4c3f83f0d)
 
 









The DHCP Server has leased out an IP address in the ranges to Webterm client
![image](https://github.com/user-attachments/assets/74af782f-3546-411c-a1d1-c142aca35cac)
![image](https://github.com/user-attachments/assets/cc27152b-42ca-425e-a5dc-75df6f804bd0)
 
 

Create a DHCP reservation
![image](https://github.com/user-attachments/assets/c826bf09-ce68-48c8-bf73-ce8ae5cfe022)
![image](https://github.com/user-attachments/assets/4d46b73d-1f29-4082-bf78-5d4cba7632b5)
 
 

DHCP_Realy

After configuring DHCP server the next thing that we will need is DHCP relay.
We use DHCP relay when our DHCP server is not in the same network as our DHCP clients.
What will happen when we configure our FortiGate firewall as a DHCP relay is that it will start to forward
all DHCP requests received from clients to the external DHCP server so with that being said let us see together how to setup this.

First we will need to make some changes in our topology so in our topology I will have to add a DHCP server.
So the DHCP server can be anything it can be a windows server or a Linux Server or for example if your company have Infoblox that provide DHCP server to your branches, we can pretend that the server that we will use here in the topology is that server.

Now the important thing is the firewall should be able to reach that DHCP server so if it is a local DHCP in our site or it is a DHCP server in a remote location, the important thing is that our firewall should reach it.
Okay, so in our case I will use the Cisco router as a DHCP server.

![image](https://github.com/user-attachments/assets/129225b9-c37d-49c3-8ba7-7cccf1701cb6)

 
Now I will connect my Cisco router to my FortiGate port two.
Now for port two side the port that is connecting the firewall with our DHCP server.

The subnet that I will use here is 172.16.10.0/24 and I will give my firewall 172.16.10.1/24 and my router 172.16.10.10/24 of course, in our LAN side where our port one is connected to our web term and our VPC, the subnet here is 192.168.1.0/24.

So what we have to do is to create a DHCP pool of this subnet in our router.
And we have to configure DHCP relay in our firewall so all our clients DHCP requests will be forwarded by our firewall to our DHCP server which is outside of this network because it’s on a different subnet.So perfect.
Let me log in with to the router.
















# Router Configuration and check DHCP Configuration
![image](https://github.com/user-attachments/assets/86041ebe-9090-420c-9b2c-fd3121112f1e)
 

# DHCP Relay Configuration in Firewall
![image](https://github.com/user-attachments/assets/f2d50642-968a-4bd6-9fa0-c5b02d0b26b6)
 






FortiGate Firewall Port2 interfaces Configuration, and verify that the FortiGate has the correct routes to handle traffic from the Cisco Router
![image](https://github.com/user-attachments/assets/279713be-20d3-462b-a7db-819e8dbf2712)
 

We can PING our DHCP Server from our Firewall
![image](https://github.com/user-attachments/assets/4d6c14bc-2821-484b-8e77-b55e90f82c96)
 
Configure a static route on Cisco router to 192.168.1.0 subnet
![image](https://github.com/user-attachments/assets/fd16d63d-d875-493e-9c06-48ddf6bd3d91)
 
Request IP using VPC
![image](https://github.com/user-attachments/assets/7f566d2a-7248-4372-91b3-e0bc9ef4efa3)
![image](https://github.com/user-attachments/assets/e17fc90a-f8c0-40eb-a889-a74508d1f3b2)
 
 

We can se the IP address issued by our DHCP server below, when FortiGate Firewall receives the DHCP requests from clients, it will generate
a new DHCP request and send it to the DHCP server.
That new request is sent by the firewall to the DHCP server via an active route in our routing table this means when the firewall receives the DHCP request, it will create a new DHCP server using the IP of the interface port one, and this request will be sent to our DHCP server based on our routing table.
![image](https://github.com/user-attachments/assets/39f67fb7-5d48-44e3-b413-11e7e734db06)
 
 
If we look at our FortiGate FW notice the routing monitor, that’s how Firewall know where to forward traffic.
![image](https://github.com/user-attachments/assets/7ddec8ad-c14c-463f-9697-9a8f7da84f29)
 
Enable Local In Policy
![image](https://github.com/user-attachments/assets/a247693b-6090-4fe0-a119-a2e80a02ad73)
 

To understand more how DHCP relay works let us go to this link here and let us start a packet capture and let us wait for the packet capture to start and now I will go and request once again an IP.
![image](https://github.com/user-attachments/assets/111fe628-3c51-4b6f-a800-08829080c418)
 


Let's wait for this to finish we can see this is our DHCP process.
 So this is the DORA Discover Offer Request and Ack.
This is the DORA process.
![image](https://github.com/user-attachments/assets/599523b9-5144-4ffd-a62b-d2e875aa6fa6)


## Fortigate Internet Access ##


Edit port 3
![image](https://github.com/user-attachments/assets/a3231d5f-c805-40b6-925f-24198f605ce5)
 ![image](https://github.com/user-attachments/assets/44183060-ab12-4c25-90b8-53a3ef635b1b)


 

WAN is selected now we give it a static IP address
![image](https://github.com/user-attachments/assets/c2e8c61d-a4a5-4b58-92e9-81a0253e8a04)
 
# Create Default Static Route
![image](https://github.com/user-attachments/assets/4291e91f-fe8e-4dc1-9191-5793361b45b9)
![image](https://github.com/user-attachments/assets/23e70354-68c2-4123-8ebc-4e34c999922b)
 
 

# INTERNET POLICY
![image](https://github.com/user-attachments/assets/eaad47e9-6ad1-4005-975c-0d005b326a41)
![image](https://github.com/user-attachments/assets/9b916ebd-b96f-478d-a8e9-f13e3f3c0ce2)
 
 


Email Alerts

## Custom SMTP server (Gmail)
![image](https://github.com/user-attachments/assets/e5b0e8ef-a12f-4f8d-9594-060f25ff5ee4)
![image](https://github.com/user-attachments/assets/0863ea8e-9d56-4dfa-8ac0-908d97cf0c40)
 
 

Setting up Events Alerts ##
![image](https://github.com/user-attachments/assets/bcef1535-1431-4cdf-9a60-5b32a07b9e2e)
![image](https://github.com/user-attachments/assets/70c4ac49-2dab-4d43-8790-4391ba3aa456)
![image](https://github.com/user-attachments/assets/88ee74b1-28d0-49e6-9452-8e6b1a0f0411)
![image](https://github.com/user-attachments/assets/156020ba-f60f-44f4-9d12-5e218aeb6034)


 
 
 
 
Email Alerts Enabled
![image](https://github.com/user-attachments/assets/6d74a752-06fb-48c1-b5d6-205956f80da4)
 


#### Traffic Shaping ####
- We use traffic shaping when we want to control our bandwidth usage.
![image](https://github.com/user-attachments/assets/b92b18bc-287e-4ad5-9814-52073560f681)
 

- we have two types of shapers.

* Per-IP: our user (IP@) use the whole shaper bandwidth. 

* Shared: in shared our shaper bandwidth by devide it to all users.


## Traffic Shaping Configuration ##

* Per-IP
![image](https://github.com/user-attachments/assets/8760e3b1-9d87-4f13-b65d-afdece32c1d8)
 

* Shared
![image](https://github.com/user-attachments/assets/f55c8bdc-5199-4ca5-a003-dc4cad33dbcd)
 

 

* Shaping Policy

 
 

 
