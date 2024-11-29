# Configurando servidor DNS

## Entre como administrador (ou use sudo para executar os comandos)

```bash
sudo su
```

## Instalar serviço

```bash
apt install bind9
```

## Acessar hosts

```bash
nano /etc/hosts
nano /etc/hostname

# Nome do servidor
hostname -f
hostnamectl

# IP do servidor
hostname -I
```

## Alterar hostname

```bash
hostnamectl set-hostname <NOME_DESEJADO>
```

### Atualizar /etc/hosts

```bash
nano /etc/hosts
```

**Abaixo de localhost, ponha:**

```conf
127.0.0.1 localhost
127.0.0.1 computeria
```

### Reiniciar máquina

```bash
reboot
```

## Acesse o diretório de configurações

```bash
cd /etc/bind
```

### Os `named.conf` são as zonas, existem três desses:

- default-zones
- local
- options # Configurações

### 1. Options

```bash
nano named.conf.options
```

```options
listen-on port 53 {<ip-configurado\>;}; # Bote seu ip
```

**Atualizar configurações**

```shell
named-checkconf
```

### 2. Local (criar zonas locais, então os nomes vão ser primeiro procurados aqui antes de procurar na internet)

Acesse o arquivo e ponha as configs do [arquivo de exemplo](02-named.conf.local):

```bash
nano named.conf.local
```

Após isso, atualize o serviço

```bash
named-checkconf
systemctl status bind9
```

## Criar zonas

### Copie o arquivo `/etc/bind/db.local`, e na cópia faça as configurações descritas em [03-db.minharede.local](03-db.minharede.local)

```bash
cp /etc/bind/db.local /etc/bind/db.minharede.local # Copiar arquivo padrão
nano /etc/bind/db.minharede.local # Coloca as configuações do arquivo que txt que tá aqui no repositório
```

Agora execute o comando para gerar zona

```bash
named-checkzone minharede.local /etc/bind/db.minharede.local # É pra aparecer OK
```

## Reiniciar e testar

```bash
named-checkconf
systemctl restart bind9
systemctl enable bind9
```

## Comando que exibe informações sobre o dns:

```bash
dig -t soa minharede.local
```

---

[Voltar ao início](/README.md)
