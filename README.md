All roles create and testing for Ubuntu 

-----------------------------------
sudo vim /etc/sysctl.conf
net.ipv4.ip_forward = 1
sudo sysctl -p
-----------------------------------
sudo nano /etc/default/ufw

DEFAULT_FORWARD_POLICY="ACCEPT"
-----------------------------------
sudo ufw allow 1194/udp
sudo ufw allow 22
-----------------------------------
sudo ufw enable
-----------------------------------
ip route list default
-----------------------------------
sudo vim /etc/ufw/before.rules

# START OPENVPN RULES
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 10.1.0.0/24 -o <iface> -j MASQUERADE
COMMIT
# END OPENVPN RULES
-----------------------------------