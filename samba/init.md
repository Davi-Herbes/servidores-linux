## Para fazer:

1. Instalar pacotes
2. Preparar diretórios
3. Preparar permissões
4. Criar os compartilhamentos em "/etc/samba/smc.conf"
5. Criar as contas de usuário do Samba
6. Proteger o Compartilhamento do Samba

## Pacotes

```
apt install samba cifs-utils samba-client
```

## Configurações

```
cd /etc/samba
```

## Criar usuários (se quiser criar um por um pode também)

```
## Criar várias contas
for i in davi luft paz; do useradd $i; done

## Criar grupo
groupadd raio

## Adicionar contas nos grupos
for i in davi luft paz; do usermod -aG raio $i; done

## Adicionar senhas pros users (vai pedir senha para cada um)
for i in davi luft paz; do smbpasswd -a $i; done
```

## Criar diretório para o samba

```
mkdir -p /data/compartilhado

## Só o grupo raio tem permissões para o diretório
chgrp raio /data/compartilhado

## Fala as permissões que os usuários têm
chmod g=rwx /data/compartilhado
```

## Adicionar diretório no samba.conf

```
nano /etc/samba/smb.conf
```

## Restartar

```
systemctl status smbd
systemctl restart smbd
systemctl enable smbd
```

## Desligar firewall

```

## Normal
sudo ufw allow Samba

## Com selinux
setenforce 0
systemctl stop firewalld
```

## Siga o arquivo client.md para acessar os items compartilhados com base no sistema operacional
