Accenture

@C1:
Conf t
vlan 20
name ACCENTURE.COM
Interface vlan 20
 desc ACCENTURE.COM
 no shut
 ip add 10.0.0.129 255.255.255.128
ip dhcp excluded-add 10.0.0.129 10.0.0.139
ip dhcp pool ACCENTURE.COM
 network 10.0.0.128 255.255.255.128
 default-router 10.0.0.129
 domain-name ACCENTURE.COM
Int e1/0
no shut
switchport mode access
switchport access vlan 20

@S1
config t
Int e1/0
no shut
ip add dhcp
do bp

**** For Chevron***
@C1:
Conf t
vlan 21
name CHEVRON.COM
Interface vlan 21
 desc CHEVRON.COM
 no shut
 ip add 10.0.8.1 255.255.248.0
ip dhcp excluded-add 10.0.8.1 10.0.8.100
ip dhcp pool CHEVRON.COM
 network 10.0.8.0 255.255.248.0
 default-router 10.0.8.1
 domain-name CHEVRON.COM

@a1
conf t
Int e0/0
no shut
switchport mode access
switchport access vlan 21
do sh vlan br

@P1
config t
Int e0/0
no shut
ip add dhcp
do bp
do dh ip domain



**** For Shell***
@C1:
Conf t
vlan 22
name SHELL.COM
Interface vlan 22
 desc SHELL.COM
 no shut
 ip add 10.0.16.1 255.255.240.0
ip dhcp excluded-add 10.0.16.1 10.0.16.100
ip dhcp pool SHELL.COM
 network 10.0.16.0 255.255.240.0
 default-router 10.0.16.1
 domain-name SHELL.COM
do sh run | sec dhcp

@a2
conf t
Int e1/0
no shut
switchport mode access
switchport access vlan 22
do sh vlan br

@P2
config t
Int e1/0
no shut
ip add dhcp
do bp
do sh ip domain

***For Fuel Save****

@C1:
Conf t
vlan 23
name FUELSAVE.COM
Interface vlan 23
 desc FUELSAVE.COM
 no shut
 ip add 10.0.2.1 255.255.254.0
ip dhcp excluded-add 10.0.2.1 10.0.2.100
ip dhcp pool FUELSAVE.COM
 network 10.0.2.0 255.255.254.0
 default-router 10.0.2.1
 domain-name FUELSAVE.COM
do sh run | sec dhcp

@C2
conf t
Int e1/0
no shut
switchport mode access
switchport access vlan 23
do sh vlan br

@S2
config t
Int e1/0
no shut
ip add dhcp
do bp
do sh ip domain



