# Configuração ssh

## Atualizar o Sistema

É importante atualizar o sistema para garantir que todos os pacotes estejam nas versões mais recentes.

`sudo apt update && sudo apt upgrade -y`

## Gerar e Usar Chaves SSH

Para uma segurança adicional, você pode configurar autenticação com chave pública.

1. No cliente, gere um par de chaves (se ainda não tiver um):

`ssh-keygen -t rsa -b 4096`

2. Copie a chave pública para o servidor (substitua `usuario` e `IP_do_servidor` conforme necessário):

`ssh-copy-id usuario@IP_do_servidor`

## Instalar o Servidor SSH

O pacote `openssh-server` fornece o daemon SSH necessário para aceitar conexões SSH.

`sudo apt install openssh-server -y`

Verifique se a instalação foi bem-sucedida:

`ssh -V # Exibe a versão do SSH instalada`

## Configurar o SSH

O arquivo de configuração principal do SSH está localizado em `/etc/ssh/sshd_config`.

### Configurações Básicas

Abra o arquivo de configuração com um editor de texto, como o Nano:

`sudo nano /etc/ssh/sshd_config`

Edite os seguintes parâmetros para configurá-los de forma segura:

`Port 2222` O padrão é 22. Para segurança adicional, você pode alterar para uma porta não usual (ex.: 2222).

`PermitRootLogin no` Desabilita o login do usuário root para maior segurança.

`PasswordAuthentication yes` Mantenha habilitada para permitir login com senha.

## Reiniciar o Serviço SSH

`sudo systemctl restart ssh`

`sudo systemctl status ssh`

## Permitir SSH no Firewall (Opcional)

`sudo ufw allow 2222/tcp # Substitua '2222' pela porta configurada`

`sudo ufw enable`

## Testar a Conexão SSH

A partir de um outro dispositivo na mesma rede, tente conectar ao seu servidor SSH:

`ssh usuario@IP_do_servidor -p 2222`

Substitua `usuario` pelo nome de usuário e `IP_do_servidor` pelo endereço IP do servidor Lubuntu. Se a porta foi alterada, especifique-a com `-p`.
