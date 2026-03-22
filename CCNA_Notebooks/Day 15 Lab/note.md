*R1
en
conf t
int g0/1
    ip address 192.168.5.126 255.255.255.128
    no shut
    do sh ip int g0/1

*PC2 -> config -> Gateway 192.168.5.126
    -> FastE -> IPAddress 192.168.5.1
    -> SubnetMask 255.255.255.128

*R1
int g0/0
    ip add 192.168.5.190 255.255.255.192
    no shut
    do sh ip int

*PC1 -> config ->Gateway 192.168.5.190
    -> FastE -> IPAdd 192.168.5.129
        ->SubnetMask 255.255.255.192

*R2
en
conf t
int g0/0
    ip add 192.168.5.206 255.255.255.240
    no shut
    do sh ip int g0/0

PC3 -> config -> Gateway 192.168.5.206
        >FastE -> IP Add 192.168.5.193
            ->Sub 255.255.255.240

*R2
int g0/1
    ip add 192.168.5.222 255.255.255.240
    no shut 
    do sh ip int g0/1

*R1
int g0/0/0
    ip add 192.168.5.225 255.255.255.252
    no shut
    do sh ip int g0/0/0

*R2
int g0/0/0
    ip add 192.168.5.226 255.255.255.252
    no shut
    do sh ip int g0/0/0

exit
ip route 192.168.5.128 255.255.255.192 192.168.5.225
ip route 192.168.5.0 255.255.255.128 192.168.5.225
do sh ip route

*R1
exit
ip route 192.168.5.192 255.255.255.240 192.168.5.226
ip route 192.168.5.208 255.255.255.240 192.168.5.225
do sh ip route

*PC1
ping 192.168.5.209
