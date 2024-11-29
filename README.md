# Relatórios de configuração de servidores linux com ubuntu

## Davi Matos, João Luft, Felipe Paz - 2 TI - IFRS Campus Feliz

### **Configurações disponíveis:**

### Recomendamos configurar os serviços na seguinte ordem:

- [ip](ip/01-configuracao.md)
- [dchp](dhcp/01-dhcp.md)
- [dns](dns/01-dns.md)
- [apache](apache/01-apache.md)
- [samba](samba/01-samba-server.md)
- [ftp](ftp/init.md)
- [ssh](ssh/01-ssh.md)

> **ℹ️** Partiremos do pressuposto de que o usuário terá as permissões de _super user_, no entanto o uso de sudo antes de determinados comandos pode se tornar obrigatório.

> **ℹ️** Usaremos o nano como editor de texto, mas sinta-se à vontade para usar vim ou algum outro.

| ⚠ Aviso                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O relatório foi projetado para funcionar em servidores baseados em ubuntu (provavelmente sistemas derivados de Debian também funcionam), portanto não recomendamos as configurações para outros sistemas operacionais. |

## Referências

- **DHCP:** https://www.isc.org/dhcp/
- **DNS:** https://bind9.readthedocs.io/en/latest/
- **Apache:** https://httpd.apache.org/docs/
- **Samba:** https://www.samba.org/samba/docs/
- **VSFTP:** https://security.appspot.com/vsftpd.html
- **SSH:** https://www.openssh.com/manual.html
