# Configuração de IP

## Acesse o diretório de configurações de rede:

```bash
cd /etc/netplan/
```

> ⚠ Caso não encontre, pode estar em `/etc/network/interfaces`, nesse caso, as configurações vão ser outras

## Vai um arquivo parecido com: `01-netcfg.yaml`:

```yaml
network:
  version: 2
  renderer: networkd # Software que irá aplicar as configurações no server
  ethernets:
    dhcp: yes/no # Se sim, a placa vai receber ip do servidor dhcp
    addresses: [10.0.0.50/24] # Define o endereço e a máscara
    gateway4: 192.168.0.1 # Define gateway (pra aula não precisa)

    # Servidores DNS:
    nameservers:
      adressess: [8.8.8.8]
```

## Atualizar redes para funcionar

```bash
netplan apply
```

---

[Comandos úteis para rede](02-comandos-ip.md) | [Informações sobre nome da placa de rede](03-nome-de-placa.md)

[Voltar ao início](/README.md)
