# &#x09;				    **Cisco Packet tracer Configuration**







Note------ 



Use "**Copper cross-over cable"** for Router to Router connection



Use "Copper straight through cable" for one component to another components connection



\####################################################################(**Router 1 Configuration**)#####################################################################



enable

conf t



interface g0/2

&#x20;ip address 10.0.0.1 255.255.255.0

&#x20;no shutdown



interface g0/1

&#x20;ip address 172.16.0.1 255.255.255.0

&#x20;no shutdown



! routes to LAN \& DMZ via R2

ip route 192.168.1.0 255.255.255.0 172.16.0.2

ip route 192.168.2.0 255.255.255.0 172.16.0.2

end





\##################################################################(**Router 2 Configuration)**#######################################################################



enable

conf t



interface g0/0

&#x20;ip address 172.16.0.2 255.255.255.0

&#x20;no shutdown



interface g0/1

&#x20;ip address 192.168.2.1 255.255.255.0

&#x20;no shutdown



interface g0/2

&#x20;ip address 192.168.1.1 255.255.255.0

&#x20;no shutdown



! default route back to R1

ip route 0.0.0.0 0.0.0.0 172.16.0.1

end



\###########################################################**(Firewall ACL Configuration for Router 2)##################################################################**



conf t

no access-list 100



access-list 100 permit icmp any host 192.168.2.10

access-list 100 permit tcp any host 192.168.2.10 eq 80

access-list 100 permit tcp any host 192.168.2.10 eq 443

access-list 100 deny ip any 192.168.1.0 0.0.0.255

access-list 100 permit ip any any



interface g0/0

&#x20;no ip access-group 100 in

&#x20;ip access-group 100 in

end



\###########################################################**TEST (ping test) IN THIS EXACT ORDER####################################################################**



From Laptop:

Step 1

ping 10.0.0.1



✔️ MUST work



Step 2

ping 172.16.0.2



✔️ MUST work



Step 3 (KEY TEST)

ping 192.168.2.10



✔️ MUST work



ping 192.168.1.10



Fails or unreachable ❌

