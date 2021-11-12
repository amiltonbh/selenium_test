Passo 1 – Pre-requisitos
Ubuntu 20.04 com Internet

Digite os comandos no terminal Linux:

# sudo apt update 
# sudo apt install -y unzip xvfb libxi6 libgconf-2-4 

Agora, iremos instalar o Java:

# sudo apt install default-jdk 

Passo 2 – Instalar Google Chrome
Para instalar a ultima versão do Google Chrome, iremos utilizar os comandos a baixo:

# sudo curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add 
# sudo bash -c "echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' >> /etc/apt/sources.list.d/google-chrome.list" 
# sudo apt -y update 
# sudo apt -y install google-chrome-stable 

Passo 3 – Instando ChromeDriver

Vamos localizar a versão do seu google chrome com o comando:

# google-chrome --version 

exemplo de saída:
Google Chrome 94.0.4606.71

Conforme a sua versão você deve digitar o comando a baixo:

# wget https://chromedriver.storage.googleapis.com/94.0.4606.61/chromedriver_linux64.zip 
# unzip chromedriver_linux64.zip 
# sudo mv chromedriver /usr/bin/chromedriver 
# sudo chown root:root /usr/bin/chromedriver 
# sudo chmod +x /usr/bin/chromedriver 

Passo 4 – Download dos arquivos Jar 
Para iniciar o download digite o comando:
# wget https://selenium-release.storage.googleapis.com/3.141/selenium-server-standalone-3.141.59.jar 
# mv selenium-server-standalone-3.141.59.jar selenium-server-standalone.jar 
# wget http://www.java2s.com/Code/JarDownload/testng/testng-6.8.7.jar.zip 
# unzip testng-6.8.7.jar.zip 

Passo 5– Iniciar Chrome via Selenium Server

inicie Chrome via Selenium Server digitando o comando:

# xvfb-run java -Dwebdriver.chrome.driver=/usr/bin/chromedriver -jar selenium-server-standalone.jar 

Para iniciar o chromedriver no terminal, digitar: 

# chromedriver --url-base=/wd/hub 


Passo 6 – Utilize os texte do nosso repositório:

O sistema já encontra instalado no seu computador, agora é só iniciar os teste com os códigos do nosso repositório. 

Antes de executar, digite o comando:

# export CLASSPATH=".:selenium-server-standalone.jar:testng-6.8.7.jar" 
# javac arquivo_de_teste.java 
# java arquivo_de_teste 

Agora é só acompanhar os resultados.


# selenium_test
