# Ubuntu (mas acho que pra CentOS também vai)

## Instalar pacote

`apt install isc-dhcp-server`

## Arquivo de configuração do isc-dhcp-server

`nano /etc/default/isc-dhcp-server`

### Bota a interface que você quer

**Vai ter INTERFACESv4 e v6, tira tudo e põe INTERFACES**\
`INTERFACES=enp2s0` <-- Bota a placa de rede que você quer que distribua os endereços

## Diretórios de configurações do dhcp

`/etc/dhcp`

## Fazer cópia do original (Se tiver, se não cria manualmente)

`mv dhcpd.conf dhcpd.conf.bk`

## Configurar

`nano /etc/dhcp/dhcpd.conf`

## Reiniciar serviço e checar

`systemctl restart isc-dhcp-server`
`systemctl status isc-dhcp-server`
