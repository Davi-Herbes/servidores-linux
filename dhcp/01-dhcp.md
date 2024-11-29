# Configurando servidor DHCP

## Entre como administrador (ou use sudo para executar os comandos)

```bash
sudo su
```

## Instalar pacote

```bash
apt install isc-dhcp-server
```

## Abra o arquivo de configuração do isc-dhcp-server

```bash
nano /etc/default/isc-dhcp-server
```

### Vai ter `INTERFACESv4` e `INTERFACESv6`, apague tudo e põe INTERFACES:

```conf
INTERFACES=enp2s0 # Nome da placa de rede que você quer que distribua os endereços
```

## Acesse o diretório de configurações do dhcp

```bash
cd /etc/dhcp
```

## Faça cópia do original (Se tiver, se não cria manualmente)

```bash
mv dhcpd.conf dhcpd.conf.bk
```

## Configurar

### Acesse o arquivo de configuração:

```bash
nano /etc/dhcp/dhcpd.conf
```

### Coloque as configurações descritas em [02-dhcpd.conf](02-dhcpd.conf)

## Reiniciar serviço e checar

```bash
systemctl restart isc-dhcp-server
systemctl status isc-dhcp-server
```

---

[Voltar ao início](/README.md)
