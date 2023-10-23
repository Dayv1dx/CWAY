# Passo a passo de como subir ONTs

1. **Fazer login na OLT no _privilege mode_**

2. **Entrar no _diagnose_**

3. **Configurar as credenciai FTP server**

~~~ bash
ftp set 
~~~

4. **Rodar o seguinte comando:**

~~~ bash
# ont-load info configuration {nome_arquivo.xml} {ftp/sftp/tftp} {ip address}

  ont-load info configuration changeNCEUrl.xml ftp 10.168.152.168
~~~

5. **Carregar o script**
~~~ bash
# load script {ftp/sftp/tftp} {ip address}

  load script ftp 10.168.152.168
~~~ 

6. **Selecionar as ONTs**

~~~ bash
# ont-load select {frame/slot port ont-id}

  ont-load select 0/1 6 1
~~~ 

7. **Carregar as ONTs**

~~~ bash
# ont start

  ont-load start
~~~ 



