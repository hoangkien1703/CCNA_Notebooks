*PC1 -> Gateway
     -> Config -> FastEthernet0/1 -> IP Address [IP_ADDRESS] [SUBNET_MASK]

*R1
en
conf t
hostname

interface g0/1
    ip address
    description ## to SW1 ##
    no shut

int g0/0
    ip address
    description ## to R2 ##
    no shut

do sh ip int brief

*R2
en
conf t
hostname
int g0/0
    ip address
    description ## to R1 ##
    no shut

int g0/1
    ip address
    description ## to R3 ##
    no shut
do sh ip int br

*R3
en
conf t
hostname
int g0/0
    ip address
    description ## to R2 ##
    no shut

int g0/1
    ip address
    description ## to SW2 ##
    no shut
do sh ip int br

PC2 -> Config -> Gateway
    -> FastEthernet0 -> IP Address

***Step 2
*R1
    exit 
    ip route 192.168.3.0 255.255.255.0 192.168.12.2
    do show ip route

*R2
    ip route 192.168.1.0 255.255.255.0 g0/0
    ip route 192.168.3.0 255.255.255.0 192.168.13.3
    do show ip ro

*R3
    exit
    ip route 192.168.1.0 255.255.255.0 192.168.13.2
    do show ip route

*PC1
    ping 192.168.3.1

