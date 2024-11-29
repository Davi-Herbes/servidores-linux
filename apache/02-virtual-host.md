# Configurando Virtual Hosts

## Crie os sites que serão servidos:

Crie os diretórios onde os sites serão armazenados com seus html base:

```bash
sudo mkdir -p /var/www/meu-site
nano /var/www/meu-site/index.html # Edite como quiser


sudo mkdir -p /var/www/meu-site2
nano /var/www/meu-site2/index.html # Edite como quiser
```

## Entre no diretório `sites-available` e crie um novo arquivo:

```bash
cd /etc/apache2/sites-available
touch teste.com.conf
```

## Configure-o da seguinte forma:

```apache
<VirtualHost 10.0.0.50:80>
    ServerName minharede.local
    DocumentRoot /var/www/meu-site
</VirtualHost>

<VirtualHost 10.0.0.50:80>
    ServerName outro.local
    DocumentRoot /var/www/meu-site2
</VirtualHost>
```

## Ativar e desativar um único site com a2ensite e a2dissite

```bash
# Entre no diretório

cd /etc/apache2/sites-available # Sites que estão disponíveis para ativar ou desativar


# Ativar (enable) site
a2ensite teste.com.conf
systemctl reload apache2

ls /etc/apache2/sites-enable # Listará pasta que contém os sites ativos

___________________________________________________________________________________________


# Desativar (disable) site
a2dissite teste.com.conf
systemctl reload apache2

ls /etc/apache2/sites-enable # Listará pasta que contém os sites ativos
```

## Próximo passo

[Instale módulos adicionais para configurações futuras](02-virtual-host.md)
