# Servidor-Web-Radio-Azucast-Docker-Ubuntu-Server-22

O AzuraCast é baseado em Docker e utiliza imagens pré-construídas que contêm todos os componentes do software. Não se preocupe se você não estiver familiar com o Docker; nossas ferramentas fáceis de instalação irão cuidar da instalação do Docker e do Docker Compose para você, e as atualizações são bem simples.

## Requisitos do Sistema

Antes de instalar, verifique a página com os requisitos de sistema do AzuraCast para garantir que o seu servidor atenda às exigências mínimas.

## Instalação

1. Conecte-se ao servidor ou computador onde deseja instalar o AzuraCast através de um terminal SSH. Você deve ser um usuário administrador com acesso root ou poder usar o comando sudo. Se você não for o usuário root, pode ser necessário executar `sudo su -` antes de executar os comandos abaixo.

2. Escolha um diretório base no seu computador host que o AzuraCast possa usar. Se você estiver no Linux, siga os passos abaixo para utilizar o diretório recomendado:

```
mkdir -p /var/azuracast
cd /var/azuracast
```

3. Use estes comandos para baixar o Script Utilitário Docker, torná-lo executável e depois executar o processo de instalação do Docker:

```
curl -fsSL https://raw.githubusercontent.com/AzuraCast/AzuraCast/main/docker.sh > docker.sh
chmod a+x docker.sh
./docker.sh install
```

4. Instruções na tela mostrarão o progresso da instalação.

## Quase pronto...

1. Assim que a instalação for concluída, abra a URL da sua instalação do AzuraCast no navegador para criar sua conta de superadministrador e finalizar a configuração inicial.

## Solução de problemas

Alguns provedores de Servidor Virtual Privado (VPS) às vezes fornecem versões antigas do Docker ou Docker Compose com seus sistemas, e a versão pode não ser totalmente compatível com o nosso script de instalação. Isso pode ser resolvido executando estes comandos e سپس tentando o processo de instalação novamente:

```
cd /var/azuracast
./docker.sh install-docker
./docker.sh install-docker-compose
./docker.sh install
```

## Instalação autônoma

Para automatizar o processo de instalação do AzuraCast, você pode executar os seguintes comandos ou colocá-los em um script cloud-init:

```
mkdir -p /var/azuracast
cd /var/azuracast
curl -fsSL https://raw.githubusercontent.com/AzuraCast/AzuraCast/main/docker.sh > docker.sh
chmod a+x docker.sh

# Para instalar o canal de lançamento "Stable" ao invés de "Rolling Release", descomente esta linha:
# yes 'Y' | ./docker.sh setup-release

yes '' | ./docker.sh install
```
