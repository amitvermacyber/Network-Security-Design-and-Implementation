# &#x09;						**OPEN VPN SETUP GUIDE** 



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_Commands \& Configuration for OpenVPN server**



sudo apt update



sudo apt install openvpn easy-rsa -y



sudo cp /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz /etc/openvpn/



cd /etc/OpenVPN



sudo gunzip server.conf.gz



\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_EDIT SERVER CONFIG



sudo nano /etc/openvpn/server.conf

\-------------------------------------------------------------------------------

Paste this code:

\-------------------------------------------------------------------------------



port 1194

proto udp

dev tun



ifconfig 10.8.0.1 10.8.0.2



secret /etc/openvpn/server/ta.key



keepalive 10 60

persist-key

persist-tun



verb 3



👉 Save (CTRL+X → Y → Enter)



\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_GENERATE KEY (CORRECT WAY)



sudo openvpn --genkey secret /etc/openvpn/ta.key



sudo systemctl start openvpn@server



sudo systemctl status openvpn@server



👉 Now it should show:



active (running) ✅





**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_Commands \& Configuration for OpenVPN client**


**use another terminal** 



sudo nano client.ovpn



\--------------------------------------------------------------------

Paste this code:

\---------------------------------------------------------------------



&#x20;                                                                  

dev tun

proto udp

remote 127.0.0.1 1194



ifconfig 10.8.0.2 10.8.0.1



secret /home/kali/ta.key



data-ciphers AES-256-CBC

verb 3



👉 Save (CTRL+X → Y → Enter)



sudo openvpn --config client.ovpn



ifconfig



👉 You should see:



tun0 

------------------------------------------------------------------->



I have mentioned the all working commands if any command fails, either take help from google and chatgpt either email me.



