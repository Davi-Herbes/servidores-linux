# Configuração ssh

## Instalar o Servidor SSH

O pacote `openssh-server` fornece o daemon SSH necessário para aceitar conexões SSH.

```bash
sudo apt install openssh-server -y
```

Verifique se a instalação foi bem-sucedida:

```bash
ssh -V # Exibe a versão do SSH instalada
```

## Configurar o SSH

O arquivo de configuração principal do SSH está localizado em `/etc/ssh/sshd_config`.

### Configurações Básicas

Abra o arquivo de configuração com um editor de texto, como o Nano:

```bash
sudo nano /etc/ssh/sshd_config
```

Edite os seguintes parâmetros para configurá-los de forma segura:

`Port 2222` O padrão é 22. Para segurança adicional, você pode alterar para uma porta não usual (ex.: 2222).

`PermitRootLogin no` Desabilita o login do usuário root para maior segurança.

`PasswordAuthentication yes` Mantenha habilitada para permitir login com senha.

## Gerar e Usar Chaves SSH

Para uma segurança adicional, você pode configurar autenticação com chave pública.

```bash
# 1. No cliente, gere um par de chaves (se ainda não tiver um):

`ssh-keygen -t rsa -b 4096`

# 2. Copie a chave pública para o servidor:

`ssh-copy-id usuario@IP_do_servidor`
```

## Reiniciar o Serviço SSH

```bash
sudo systemctl restart ssh

sudo systemctl status ssh
```

## Permitir SSH no Firewall (Opcional)

```bash
sudo ufw allow 2222/tcp # Substitua '2222' pela porta configurada

sudo ufw enable
```

## Testar a Conexão SSH

A partir de um outro dispositivo na mesma rede, tente conectar ao seu servidor SSH:

```bash
ssh usuario@IP_do_servidor -p 2222
```

## Conclusão

Seguindo esses passos, já é possível ter configurações funcionais de um servidor ssh com chave pública. [Volte ao início](/README.md) para realizar outras instalações
