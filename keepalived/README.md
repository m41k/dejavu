 yum install -y keepalived
 
<pre> 
Configuração do servidor 1:
server1# cat /etc/keepalived/keepalived.conf
vrrp_instance VI_1 {
 state MASTER
 interface eth0
 virtual_router_id 51
 priority 255
 advert_int 1
 authentication {
 auth_type PASS
 auth_pass 12345
 }
 virtual_ipaddress {
 192.168.122.200/24
 }
}
Configuração do servidor 2:
server2# cat /etc/keepalived/keepalived.conf
vrrp_instance VI_1 {
 state BACKUP
 interface eth0
 virtual_router_id 51
 priority 254
 advert_int 1
 authentication {
 auth_type PASS
 auth_pass 12345
 }
 virtual_ipaddress {
 192.168.122.200/24
 }
}
