## Bootcamp Dio DevOps Provisionamento Servidor Web Apache

#### O desafio foi criar um scrpit para:
- Atualizar o servidor;
- Instalar o apache2;
- Instalar o unzip
- Baixar a aplicação disponível no endereço https://github.com/denilsonbonatti/linux-site-dio/archive/refs/heads/main.zip no diretório /tmp;
- Copiar os arquivos da aplicação no diretório padrão do apache


### Esse é o script que fiz:
```bash
#/bin/bash!

echo "Iniciando script!"

echo "Atualizando servidor..."
#Atualizar o servidor
apt update && sudo apt upgrade -y

echo "Iniciando instalações Unzip, Wget e Apache..."
sleep 3

#Instalar Unzip
apt install unzip -y

#Instalar wget
apt install wget -y

#Instalar Apache
apt install apache2 -y

#Verificar status apache
systemctl status apache2

echo "Baixando repositórios..."
sleep 3
#Baixar repositórios da aplicação e criar o diretório tmp
wget -P ~/tmp https://github.com/denilsonbonatti/linux-site-dio/archive/refs/heads/main.zip

#Extrair arquivos
unzip ~/tmp/main.zip -d ~/tmp 

echo "Copiando arquivos..."
sleep 2
#Copiar os arquivos da aplicação para o Apache
cp -r ~/tmp/linux-site-dio-main/* /var/www/html

echo "Finalizado!"
