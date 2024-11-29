# Configurando Samba Server

## Para fazer:

1. Instalar pacotes
2. Preparar diretórios
3. Preparar permissões
4. Criar os compartilhamentos em "/etc/samba/smc.conf"
5. Criar as contas de usuário do Samba
6. Proteger o Compartilhamento do Samba

## Pacotes

```bash
apt install samba cifs-utils samba-client
```

## Configurações

```bash
cd /etc/samba
```

## Criar usuários (se quiser criar um por um pode também)

```bash
# Criar várias contas
for i in davi luft paz; do useradd $i; done

# Criar grupo
groupadd raio

# Adicionar contas nos grupos
for i in davi luft paz; do usermod -aG raio $i; done

# Adicionar senhas pros users (vai pedir senha para cada um)
for i in davi luft paz; do smbpasswd -a $i; done
```

## Criar diretório para o samba

```bash
mkdir -p /data/compartilhado

## Só o grupo raio tem permissões para o diretório
chgrp raio /data/compartilhado

## Fala as permissões que os usuários têm
chmod g=rwx /data/compartilhado
```

## Adicionar diretório no samba.conf

```bash
nano /etc/samba/smb.conf
```

```ini
# * [ Configurações já existentes ]

# Adicione (ou altere se já houver):
[global]
    host allow = 0.0.0.0/0

[nome_diretório] # Nomeia o diretório no serviço do samba
    comment = comentário
    path = /data/compartilhado # ou outro nome
    write list = @raio # Nome do grupo criado
    browseable = yes

    # Os usuários não poderão só ser como escrever
    read only = no
    writable = yes
```

## Reinicie os serviços

```bash
systemctl status smbd
systemctl restart smbd
systemctl enable smbd
```

## Desligar firewall para habilitar conexões do samba

```bash

# Normal
sudo ufw allow Samba

# Com selinux
setenforce 0
systemctl stop firewalld
```

## Siga o arquivo [client.md](02-samba-client.md) para acessar os items compartilhados com base no sistema operacional

## [Voltar ao início](/README.md)
