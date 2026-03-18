*Key Principle
Switches (Layer 2): Forward frames without changing source or destination MAC addresses.
Routers (Layer 3): Re-write both source and destination MAC addresses at each hop (de-encapsulate and re-encapsulate).


The IP addresses stay the same end-to-end; only MAC addresses change at each router hop.

 Same Subnet:  SRC/DST MAC = actual source and destination hosts
                (switch just forwards)

 Different Subnet at each hop:
   SRC MAC = egress interface of the sending router (or original host)
   DST MAC = ingress interface of the next-hop router (or final host)