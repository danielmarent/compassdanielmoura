#  Cofigurar a internnet para modo Bridge

Entre nas configuraçoes da maquina linux pela vm.

Clique em rede.

Mude a opção conectado a: NAT para placa em modo bridge.

Depois volte para o Oracle

execute o comando cd /etc/sysconfig/network-scripts/ 

depois o comando sudo vi ifcfg-enp0s3

mude as configurações para BOOTPROTO=dhcp

adicione as seguintes linhas 

#IPADDR=10.0.2.15

#NETMASK=255.255.255.0

#GATEWAY=10.0.2.2

depois aperte :wq para salvar e de um reboot para reiniciar a maquina.

logo após execute o comando ip addr e veja qual e o ip fornecido pelo servidor dns.

depois volte novamente para o ifcfg-enp0s3 

mude o BOOTPROTO=dhcp para BOOTPROTO=static

apague as 3 linhas inseridas anteriormente 

#IPADDR=10.0.2.15
#NETMASK=255.255.255.0
#GATEWAY=10.0.2.2

logo após da um reboot novamente

depois execute o comando nmtui

entre na opção para editar

desabilite o ipv6

e configure o ipv4 conforme os dados que aparece o ip addr que foi coletado antes.

de um reboot novamente

depois execute o comando ping 8.8.8.8 e testará sua internet.

