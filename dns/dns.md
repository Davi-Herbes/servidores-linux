## Instalar serviço

`apt install bind9`

## Acessar hosts

`nano /etc/hosts`\
`nano /etc/hostname`\

`hostname -f ou hostnamectl` <-- nome\
`hostname -I` <-- ip

## Alterar hosname

`sudo hostnamectl set-hostname computeria`

### Aualizar /etc/hosts

`sudo nano /etc/hosts`

`127.0.0.1 localhost`
`127.0.0.1 computeria`

**Reiniciar máquina**
`sudo reboot`

## Diretório configs

`/etc/bind`

Os `named.conf` são as zonas

- default-zones
- local
- options <-- Configuraões

## options

`nano named.conf.options`

- no `listen-on port 53 {<ip-configurado\>;};` põe seu ip

`named-checkconf` <-- atualizar configs

## local (criar zonas locais, então os nomes vão ser primeiro procurados aqui antes de procurar na internet)

Põe as configs do arquivo de exemplo:\
`nano named.conf.local`

`named-checkconf` <-- atualizar configs
`systemctl status bind9`

## Criar zonas

`sudo cp /etc/bind/db.local /etc/bind/db.minharede.local` <-- Copiar arquivo padrão
`sudo nano /etc/bind/db.computeria.local` <-- Coloca as configuações do arquivo que txt que tá aqui no repositório

`named-checkzone computeria.local /etc/bind/db.computeria.local` <-- É pra aparecer OK

## reiniciar e testar

`named-checkconf`\
`systemctl restart bind9`
`systemctl enable bind9`

Vai mostrar muita coisa:
`dig -t soa computeria.local`
