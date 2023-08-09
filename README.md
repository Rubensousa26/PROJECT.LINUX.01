# PROJECT.LINUX.01
#!/bin/bash

# Atualiza o sistema
echo "Atualizando o sistema..."
sudo apt update
sudo apt upgrade -y

# Instala o servidor Apache
echo "Instalando o servidor Apache..."
sudo apt install apache2 -y

# Instala o utilitário 'unzip'
echo "Instalando o utilitário unzip..."
sudo apt install unzip -y

# Diretório temporário para download e extração
temp_dir="/tmp/linux-site-dio"

# Baixa e extrai a aplicação
echo "Baixando e copiando os arquivos da aplicação..."
mkdir -p $temp_dir
cd $temp_dir

# URL do arquivo zip da aplicação
app_zip_url="https://github.com/denilsonbonatti/linux-site-dio/archive/refs/heads/main.zip"

# Nome do diretório após a extração
app_extracted_dir="linux-site-dio-main"

# Baixa o arquivo zip da aplicação
wget $app_zip_url

# Extrai os arquivos
unzip main.zip

# Copia os arquivos para o diretório do servidor web
sudo cp -R $app_extracted_dir/* /var/www/html/

# Limpa o diretório temporário
rm -rf $temp_dir

echo "Provisionamento concluído."
