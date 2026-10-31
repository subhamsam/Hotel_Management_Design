Modern Hotel Network Design & Implementation
A multi-floor hotel network designed and implemented in Cisco Packet Tracer. The project covers VLAN segmentation, router-on-a-stick inter-VLAN routing, OSPF, DHCP, SSH remote access, and port security.
Network Topology
  

________________


Project Overview
The hotel has three floors, each with its own switch, router, and Wi-Fi network. All three routers sit in the IT server room on the third floor and are linked to each other over serial DCE connections. Every department is isolated in its own VLAN and subnet, and all devices can still communicate with each other.
Floor
	Departments
	1st
	Reception, Store, Logistics
	2nd
	Finance, HR, Sales/Marketing
	3rd
	Admin, IT
	________________


Requirements Implemented
* [x] 3 routers, one per floor, all placed in the IT server room
* [x] Routers interconnected using serial DCE cables
* [x] 1 switch per floor, placed on the respective floor
* [x] Wi-Fi network on each floor for laptops and phones
* [x] 1 printer per department
* [x] Each department in its own VLAN and subnet
* [x] OSPF to advertise routes
* [x] DHCP on each router for dynamic IP assignment
* [x] Full connectivity between all devices
* [x] SSH enabled on all routers
* [x] Test-PC in IT on port fa0/4 used to test remote login
* [x] Port security on the IT switch (sticky MAC, violation mode shutdown)
________________


Addressing Scheme
Router-to-Router Links (Serial)
Link
	Network
	Router link 1
	10.10.10.0/30
	Router link 2
	10.10.10.4/30
	Router link 3
	10.10.10.8/30
	VLANs and Subnets
Floor
	Department
	VLAN ID
	Network
	1st
	Reception
	80
	192.168.8.0/24
	1st
	Store
	70
	192.168.7.0/24
	1st
	Logistics
	60
	192.168.6.0/24
	1st 
	WIFI
	200
	192.168.20.0/24
	2nd
	Finance
	50
	192.168.5.0/24
	2nd
	HR
	40
	192.168.4.0/24
	2nd
	Sales/Marketing
	30
	192.168.3.0/24
	2nd 
	WIFI
	100
	192.168.10.0/24
	3rd
	Admin
	20
	192.168.2.0/24
	3rd
	IT
	10
	192.168.1.0/24
	3rd 
	WIFI
	300
	192.168.30.0/24
	________________


Technologies Used
* VLANs and 802.1Q trunking for department isolation
* Inter-VLAN routing (router-on-a-stick) on each floor router
* OSPF for dynamic routing between floors
* DHCP with each router acting as the DHCP server for its floor
* SSH for secure remote management
* Port security (sticky MAC, shutdown violation mode)
* Serial (DCE/DTE) links with clock rate between routers
________________


Repository Structure
.
├── README.md
├── HotelNetwork.pkt        # Packet Tracer project file
├── configs/
│   ├── R1.txt
│   ├── R2.txt
│   ├── R3.txt
│   ├── SW-Floor1.txt
│   ├── SW-Floor2.txt
│   └── SW-Floor3.txt
└── images/
    ├── topology.png
    └── ...              
________________
Verification
The screenshots for the verfications are in the Diagram folder inside folder name Verification

Connectivity
Ping between PCs in different VLANs and on different floors:
F1>F2
  

F2>F3
  

OSPF
Router# show ip ospf neighbor
Router# show ip route ospf
  



DHCP
Router# show ip dhcp binding
  

VLANs and Trunks
Switch# show vlan brief
Switch# show interfaces trunk
  





SSH
From Test-PC in the IT department:
  



Port Security
Switch# show port-security interface fa0/1
Switch# show port-security address


Connecting any device other than Test-PC to fa0/4 puts the port into an err-disabled (shutdown) state.
  

  

________________




What I Learned
* Planning a VLAN and IP addressing scheme for a multi-department network
* Configuring OSPF across serial links
* Setting up DHCP pools and inter-VLAN routing per floor
* Securing device access with SSH and switch ports with port security
________________


Author
<SOURAV MAHATO>
