# Red Hat linux


Mudar o Host name:
```
sudo hostnamectl set-hostname LinuxSRV
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

### Mudar permissões

r = ler

w = escrever

x = executar

utilizador:
```
chmod u+rwx listar
```

Groupo:
```
chmod g+rwx listar
```

Outros:
```
chmod o+rwx listar
```
# Red Hat Linux Servidor
## Instalar nginx

Instalar nginx:
```
sudo amazon -linux-extras install nginx1
```

Iniciar o serviso nginx:
```
systemctl start nginx.service 
```

Iniciar o serviso todas as vezes que a maquina for ligada:

```
systemctl enable --now nginx.service 
```

Verificar se a port 80 está aberta 
```
netstat -tapn
```
Para alterar a configuração do nginx:
```
cd /etc/nginx/
nano nginx.conf
```
## Red Hat Linux Cliente




