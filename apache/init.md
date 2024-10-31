## Instalação

```
apt install apache2
```

### Configurações apache

```
cd /etc/apache2
```

### Aplicação do site

```
cd /var/www/html
```

### Sites

```
cd /etc/apache2/sites-available

# Ver os arquivos:
ls -lah
```

### Ativar e desativar um único site com a2ensite e a2dissite

```
cd /etc/apache2/sites-available

a2ensite site.com.conf
systemctl reload apache2
ls /etc/apache2/sites-enable


a2dissite site.com.conf
systemctl reload apache2
ls /etc/apache2/sites-enable

```
