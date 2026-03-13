enable 
conf t
hostname

int
do show ip interface brief  //do sh ip int br
ip address [IP_ADDRESS] [SUBNET_MASK]
speed 1000
duplex full
description [## to SW1 ##]
no shutdown
do show ip int br

int range g0/1 - 2
description [## not in use ##]
do sh run
end

copy running-config startup-config
show startup-config

PC ->config FastEthernet0/1 ->IP Address [IP_ADDRESS] [SUBNET_MASK]

*SW1
en
conf t
host
do sh int status

int [g0/1]
speed [1000]
duplex full
description ## to R1 ##

**(do the same to g0/2)


int range f0/1 - 2
    description ## to end hosts ##

int range f0/3 - 24
    description ## not in use ##
    shutdown

end
write
show startup-config


**(do the same to SW2)
int range g0/2,f0/3-24
    description ## not in use ##
    shutdown
write
show startup-config

***(do the same to SW2)


