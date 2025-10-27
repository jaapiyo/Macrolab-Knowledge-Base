Critical interfaces between computers and controllers should not be connected through the regular local area network (LAN). These should be connected straight or with a network switch in between.
## Addressing
To prevent the devices from operating on a regular LAN we restrict the IP range of our devices to **169.254.0.0/16**. This is called a **link-local address** which is a network address that is valid only for communications on a _local link_, i.e. within a subnetwork that a host is connected to. 

Link-local addresses are not guaranteed to be unique beyond their network segment. Therefore, routers do not forward packets with link-local source or destination addresses. Thus effectively isolating the device from the rest of the network in case it were connected to a LAN.