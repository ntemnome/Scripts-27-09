# Scripts-27-09
enable
configure terminal
hostname RT-CORE
banner motd "ACESSO APENAS PARA PESSOAS AUTORIZADAS"
enable secret SenhadaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
line vty 0 15
password SenhadaVTY
login 
transport input ssh
exec-timeout 10
exit
username PedroHenrique privilege 15 secret pao
line console 0
password SenhadaConsole
login
exit
service password-encryption
interface gigabitEthernet 0/0
ip address 172.16.1.0 255.255.254.0
description RT-11
no shutdown
exit
interface gigabitEthernet 1/0
ip address 192.168.0.1 255.255.192.0
description 
no shutdown
exit
interface gigabitEthernet 2/0
ip address 192.168.72.1 255.255.252.0
description REDE 3
no shutdown
exit
interface gigabitEthernet 3/0
ip address 192.168.76.1 255.255.255.224
description REDE 4
no shutdown
do wr
