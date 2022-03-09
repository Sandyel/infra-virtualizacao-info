# Base de informações de virtualização

## Base para gerar um ambiente de virtualização
---
> - Versão do vagrant `2.2.19` [vagrant](https://github.com/Sandyel/infra-virtualizacao-info/commits/v2.2.19)
> - Link para baixa a VM VirtualBox  ---> [***Baixa aqui a VM VirtualBox***](https://www.virtualbox.org/wiki/Downloads)
>
> links para downloads de algumas imagens do linux: 
>
> [***linux.org***](https://www.linux.org/pages/download/) | Principais imagens
> 
> - [***ubuntu***](https://www.ubuntu.com/download)  [***debian***](https://www.debian.org/distrib/ftplist) [***fedora***](https://getfedora.org/)
>   [***kali***](https://www.kali.org/downloads/)
 ---
 
 ## Usando o Vagrant para subir um servidor apache
 
 É recomendado criar uma pasta para centralizar o arquivo de configuração do vagrant, pode ser com o nome : **vagrant**. 
 Após isso criar um arquivo com o nome __vagrantfile__ com o respectivo script:
 ```script
  # -*- mode: ruby ​​-*-
# vi: set ft=ruby:
# Toda a configuração do Vagrant é feita abaixo. O "2" em Vagrant.configure
# configura a versão de configuração (suportamos estilos mais antigos para
# retrocompatibilidade). Por favor, não altere a menos que você saiba o que
# está fazendo.
Vagrant.configure("2") do |config|
  config.vm.define "server" do |server|
  config.vm.box = "debian/buster64"
  server.vm.hostname = "server"
  server.vm.network "public_network"
  end  
end
 ```
 
 Após salvar o arquivo deve-se, dentro do diretório vagrant abrir com um editor de código ou via terminal, execute o comando: `vagrant up` <br>
 Após alguns minutos subindo as entrelinhas: o vagrant instancia uma nova vm. Para ver se está rodando use o comando : `vagrant status` <br>
 Para se conectar a vm que está on, use o comando: `vagrant ssh server`  <br>
 Pronto! Você está conectado a sua nova máquina que acabou de criar usando o vagrant. Mas para instalar o apache precisa está logado como usuario root. 
Sendo assim use o comando `su` que lhe dara as permissões de super usuário em seguida ele vai pedir a senha, por padrão a senha é `vagrant`. <br>
 Com isso já feito para instalar o apache use o comando: `apt-get install apache2` instalado o pacote apache2, agora o caminho é feliz \o/ ou não. <br>
 Para acessar o servidor use o comando `ip address` vai listar 3 adapitadores de rede o que interessa é o 3 é só digitar o endereço ip no navegador e visualizará o apache. <br>
 Normalmente dar um erro. Provavelmente o endereço da porta, para configurar essa parte adicione no arquivo do vagrant > vagrantfile a seguinte linha: 
 
 ![vagrantfile](https://user-images.githubusercontent.com/40548971/157384859-f0b97668-37b0-4525-9dea-06d6d3930080.png)

Depois use externamente o comando `vagrant reload`.



*fonte
[documentação no site oficial do vagrant](https://www.vagrantup.com/docs)
 
 
 
 
 
 
 
 
 
