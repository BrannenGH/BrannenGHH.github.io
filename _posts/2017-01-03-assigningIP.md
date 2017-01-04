---
layout: post
title:  "NetworkManager not able to Lease an IP from a router — How to Manually Request an IP"
date:   2017-01-03
categories: NetworkManager openSUSE SLES SLED SUSE 
permalink: /archive/networkmanager_lease_ip_manually
public: yes
---

NetworkManager may throw the error ``Error: Connection activation failed: (5) IP configuration could not be reserved (no available address, timeout, etc.).``  This means for some reason the wifi card is able to connect to the AP, but it is unable to reserve a dynamic IP with DHCP. In this guide I will explain a potential solution to the problem (particularly if it is your wifi card that is the problem and not the access point) which is to request an IP manually using ``dhclient``. 

# Step One  
In this step, we will have NetworkManager manually connect to the AP as root, I've found this step to just ensure that the system is in the right state for ``dhcleint`` to manually request an IP. This can be done by opening up a terminal, and running the following command:  
    sudo nmcli d wifi Connect $wifi_access_point_SSID password $wifi_access_point_password  
In which ``$wifi_access_point_SSID`` is the name of the network you are trying to connect to, and ``$wifi_access_point_password`` is the password to the network you are trying to connect to. After that command is executed, your wifi card should try to connect to the AP, after which it will throw the ``Error: Connection activation failed: (5) IP configuration could not be reserved (no available address, timeout, etc.).`` error. Once you have this error, you can proceed to step two.  

# Step Two  
Once ``nmcli`` has thown the error above, we can use ``dhclient`` to manually ask for an IP. This is done though the command:  
    sudo dhclient -v  
You should see ``dhclient`` request an IP, and after a few minutes, it should return ``bound: renewal in $number seconds.``, in which $number is how many seconds the lease is, which also means your wifi card was successfuly granted an IP lease!  
