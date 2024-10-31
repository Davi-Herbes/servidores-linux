# Relatório: Configuração de um Servidor FTP no Lubuntu

Este relatório descreve o processo de configuração de um servidor FTP no Lubuntu, utilizando o `vsftpd` (Very Secure FTP Daemon), que é um dos servidores FTP mais seguros e confiáveis disponíveis.

## 1. Instalação do vsftpd

Para instalar o `vsftpd`, abra um terminal e execute os seguintes comandos:

```bash
sudo apt update
sudo apt install vsftpd
```

## 2. Configuração do vsftpd

Após a instalação, é necessário editar o arquivo de configuração do `vsftpd`. Abra o arquivo de configuração com um editor de texto, como o `nano`:

```bash
sudo nano /etc/vsftpd.conf
```

### 2.1. Principais Configurações

- **Habilitar FTP Anônimo:**

  Para permitir acesso anônimo, encontre a linha que diz `anonymous_enable=NO` e altere para `YES`. Se não quiser permitir acesso anônimo, mantenha como `NO`.

- **Habilitar Usuários Locais:**

  Para permitir que usuários do sistema possam se conectar, encontre a linha `local_enable=NO` e altere para `YES`.

- **Habilitar Uploads:**

  Para permitir que os usuários façam uploads, encontre a linha `write_enable=NO` e altere para `YES`.

- **Definir Diretório Raiz dos Usuários:**

  Para restringir os usuários a suas próprias pastas, adicione a seguinte linha:

  ```bash
  chroot_local_user=YES
  ```

### 2.2. Configurações Adicionais

Dependendo de suas necessidades, você pode querer adicionar outras configurações, como limites de conexão e taxas de transferência. Para mais detalhes, consulte a documentação do vsftpd.

## 3. Reiniciando o Serviço

Depois de realizar as configurações necessárias, reinicie o serviço do `vsftpd` para aplicar as mudanças:

```bash
sudo systemctl restart vsftpd
```

## 4. Adicionando Usuários

Para adicionar um novo usuário FTP, você pode usar o comando `adduser`. Exemplo:

```bash
sudo adduser nome_do_usuario
```

Siga as instruções para definir a senha e outras informações do usuário.

## 5. Testando a Conexão FTP

Para testar a configuração, você pode usar um cliente FTP como o FileZilla ou o comando `ftp` no terminal. Conecte-se ao servidor usando o IP do servidor e as credenciais do usuário que você criou.

## 6. Verificando o Status do Serviço

Você pode verificar o status do `vsftpd` para garantir que ele está rodando corretamente:

```bash
sudo systemctl status vsftpd
```
