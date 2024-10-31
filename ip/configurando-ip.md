## Diretório de configurações de rede:

`/etc/netplan`

Antigamente ficava em:/
`/etc/network/interfaces`

## Arquivo

Vai ter algo parecido com:\
`01-netcfg.yaml`

## Dentro do bloco ethernets > placa (enp2s3 sla)

`dhcp: yes/no` // Se sim, a placa vai receber ip do servidor dhcp\
`addresses: [10.0.0.50/24]` // Define o endereço e a máscara\
`gateway4: 192.168.0.1` // Define gateway (pra aula não precisa)\
Servidores DNS:\
`nameservers:`\
&nbsp;`adressess: [8.8.8.8]`

## Atualizar redes para funcionar

`netplan apply`
