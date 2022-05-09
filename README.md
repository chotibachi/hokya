# hokya
interface Loopback0
ip address 10.1.1.1 255.255.255.0 
exit
interface Serial0/0/0
ip address 192.168.1.5 255.255.255.252 
no shutdown
end

R2
interface Loopback0
ip address 10.2.2.1 255.255.255.0 
interface Serial0/0/0
ip address 192.168.1.6 255.255.255.252 
no shutdown
exit 
interface Serial0/0/1
ip address 172.24.1.17 255.255.255.252 
no shutdown
end

R3
Churchgate(config)# interface Loopback0 
Churchgate(config-if)# ip address 10.3.3.1 255.255.255.0 
Churchgate(config-if)# exit
Churchgate(config)# interface Serial0/0/1
Churchgate(config-if)# ip address 172.24.1.18 255.255.255.252 
Churchgate(config-if)# no shutdown
Churchgate(config-if)# end
Churchgate#

R1
Andheri(config)# router bgp 100
Andheri(config-router)# neighbor 192.168.1.6 remote-as 300 
Andheri(config-router)# network 10.1.1.0 mask 255.255.255.0

R2
Bandra(config)# router bgp 300
Bandra(config-router)# neighbor 192.168.1.5 remote-as 100 
Bandra(config-router)# neighbor 172.24.1.18 remote-as 65000 
Bandra(config-router)# network 10.2.2.0 mask 255.255.255.0

R3

Churchgate(config)# router bgp 65000
Churchgate(config-router)# neighbor 172.24.1.17 remote-as 300 
Churchgate(config-router)# network 10.3.3.0 mask 255.255.255.0

R2
Bandra# show ip bgp neighbors

R1
Andheri#show ip route
ping 10.3.3.1 source 10.1.1.1 or ping 10.3.3.1 source Lo0
Andheri# show ip bgp

R2

Bandra(config)# ip as-path access-list 1 deny ^100$ 
Bandra(config)# ip as-path access-list 1 permit .*
Bandra(config)# router bgp 300
Bandra (config-router)# neighbor 192.168.1.5 remove-private-as
