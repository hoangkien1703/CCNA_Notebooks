*PC1
ping [PC2]      //Not work
ipconfig
ipconfig /all
ping [default_gateway]

*R1
en
show IP interface brief
show IP route
configue terminal
do show running-config | include ip route

no ip route 192.168.3.0 255.255.255.0 192.168.12.3
ip route 192.168.3.0 255.255.255.0 192.168.12.2
do show run | include ip route
do sh ip route



*R2
en
sh ip int br
sh ip route
conf t
no ip route 192.168.3.0 255.255.255.0 GigabitEthernet0/0
do sh ip route              //the new doesn't overwrite the old
do sh run | include ip route
ip route 192.168.3.0 255.255.255.0 192.168.13.3
do sh ip ro


*R3 
en
sh ip int br
conf t
int g0/0
    do sh run
    ip add 192.168.13.3 255.255.255.0
    do sh run 
    do sh ip route