# Red Hat linux


Mudar o Host name:
```
sudo hostnamectl set-hostname <nome>.enta.pt
```

Atualizar o sistema:
```
sudo yum update
```

Onde tu estas:
```
pwd
``` 

Entrar como root:
```
sudo su -
```

Criar uma pasta:
```
mkdir <nome_da_pasta>
```

Remover uma pasta:
```
rmdir <nome_da_pasta>
```

Remover uma pasta se não estiver vazia:
```
rm -r <nome_da_pasta>
```

# Red Hat Linux Servidor
## Instalar nginx

Instalar nginx:
```
sudo amazon -linux-extras install nginx1
```

Iniciar o serviso nginx:
```
sudo systemctl start nginx.service 
```

Iniciar o serviso todas as vezes que a maquina for ligada:

```
sudo systemctl enable --now nginx.service 
```


Verificar se a port 80 está aberta: 
```
netstat -tapn
```
Alterar a configuração do nginx:
```
cd /etc/nginx/
sudo nano nginx.conf
```

Não esquecer de reiniciar o serviso depois de alterar o nginx.conf:
```
sudo systemctl restart nginx.service 
```

Alterar o HTML: 
```
cd /usr/share/nginx/html
```

Editar os hosts para entrar nos sites:
```
nano /etc/hosts
Exemplo:
  <Ip_privado_do_servidor> www.central.pt
  <Ip_privado_do_servidor> www.ocidental.pt
  <Ip_privado_do_servidor> www.oriental.pt
```


## Instalar FTP 

Instalar ftp:
```
sudo yum install vsftpd
```

Ativar ftp:
```
sudo systemctl start vsftp
```
Iniciar o serviso todas as vezes que a maquina for ligada:
```
sudo systemctl enable --now vsftpd
```

Alterar a configuração do ftp:
```
sudo nano /etc/vsftpd/vsftpd.conf
  Descomentar e alterar:
  
    anonymous_enable=NO
    
  Adicionar:
  
    pasv_enable=YES
    pasv_min_port=1024
    pasv_max_port=1048
    
```

Não esquecer de reiniciar o serviso depois de alterar o vsftpd.conf:
```
sudo systemctl restart vsftpd
```

Adicionar os utilizadores:
```
adduser <nome_do_user>
passwd <nome_do_user>
```

Mudar o grupo de um ficheiro pu pasta:
```
chgrp -R <nome_da_pasta/ficheiro> <nome_do_grupo> <localização_da_pasta/ficeiro>
Exemplo:
  chgrp -R central central /usr/share/nginx/central/
```

### Mudar permissões

r = ler

w = escrever

x = executar

utilizador:
```
chmod u+rwx <nome_do_ficheiro/pasta>
```

Groupo:
```
chmod g+rwx <nome_do_ficheiro/pasta>
```

Outros:
```
chmod o+rwx <nome_do_ficheiro/pasta>
```


# Red Hat Linux Cliente
## Instalar o desktop

```
sudo su -
```
```
amazon-linux-extras install epel
```
```
yum groupinstall "MATE Desktop"
```
```
yum install xrdp chromium filezilla
```
```
systemctl enable --now xrdp
```
This will make all users to have the graphic interface:
```  
bash -c 'echo PREFERRED=/usr/bin/mate-session > /etc/sysconfig/desktop'
```
```
adduser <nome_do_utilizador>
passwd <nome_do_utilizador>
```
```
echo "/usr/bin/mate-session" > ~/.Xclients && chmod +x ~/.Xclients
```
```
reboot
```
Depois de reiniciar
```
sudo firewall-cmd --add-port=3389/tcp --permanent
```
```
sudo firewall-cmd --reload
```
