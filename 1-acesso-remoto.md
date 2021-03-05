# Tutorial - Acesso Remoto - CCI 2

## 1 - Instalar e configurar o OpenVPN:

### 1.1 - Instale o OpenVPN com o comando a seguir:
~~~shell
sudo apt-get update; sudo apt-get install openvpn -y
~~~

### 1.2 - Configurando o OpenVPN: 
  
    Realize o download do arquivo de configuração dentro do portal do Servidor/Aluno em: <br>
    Geral > Catálogo de Serviços > Chasque > VPN > Ativação/Informação > Link: "Somente arquivo de configuração (Multiplataforma)."**
    Após realizar o download do arquivo **VPN-UFRGS.ovpn** mova-o para o diretório do seu projeto.

## 2 - Instalar o VNC Viewer:

    Podemos baixar o VNC Viewer acessando o site: https://www.realvnc.com/pt/connect/download/viewer/


## 3 - Conectando na VPN:

### 3.1 - Abra o primeiro terminal:

- Vá até o diretório do seu projeto e digite:
~~~shell
  sudo openvpn --config VPN-UFRGS.ovpn
~~~

- Insira a senha para sudo do seu usuário;
- Após isso vai aparecer: 
  - Enter Auth Username:  **forneça o carão ufrgs**;
  - Enter Auth Password:  **forneça a senha do portal da ufrgs**;
- A confirmação da conexão é dada pela mensagem **"Initialization Sequence Completed"**;
- Enquanto este terminal permanecer aberto, a VPN estará conectada;
- Veja o exemplo:

![terminal1](/img/terminal1.png)

### 3.2 - Abra o segundo terminal (sem fechar o primeiro terminal): 

- Digite:
~~~shell
  ssh seuUsuario@pgmicro01.ufrgs.br
  # forneça a senha obtida com o formiga
~~~

- Digite:
~~~shell
  vncserver -geometry 1920x1080 -depth 24
  # forneça um password para acessar
~~~
> Note que 1920x1080 é a resolução desejada e -depth poderia ser 8, 16 ou 24

- Veja o exemplo:

![terminal2](/img/terminal2.png)

- Guarde o valor X.

### 3.3 - Abra o terceiro terminal (sem fechar os outros 2): 

- Digite:
~~~shell
  ssh -L 6000:localhost:5926 seuUsuario@pgmicro01.ufrgs.br
~~~
> Note que fizemos 5900 + X = 5926
>
> Sempre somaremos 5900 com o X.

- Veja o exemplo:
![terminal3](/img/terminal3.png)

### 3.4 - Abra o VNC Viewer:

- Conforme o valor do X digite::

![vncviewer1](/img/vncviewer1.png)

<br>

- Ao final aparecerá isto:

![vncviewer2](/img/vncviewer2.png)





