enable
configure terminal
hostname [NAME]

do show ip interface brief
interface gigabitethernet [0/0]
ip address [IP_ADDRESS] [SUBNET_MASK]
decription ## [NAME] ##
no shutdown

write


***
on PC: config -> fastEthernet0 -> IP Configuration
IP ADDRESS: [IP_ADDRESS]
SUBNET MASK: [SUBNET_MASK]
***

ping [IP]



