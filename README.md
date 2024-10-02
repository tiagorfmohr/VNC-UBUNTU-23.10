# Como Instalar o VNC no UBUNTU 23.10

Neste passo a passo você irá aprender como realizar a instalação e configuração do acerro remoto através do VNC.

##### [Neste link está disponível do passo a passo em vídeo](https://www.youtube.com/watch?v=A7R-mZQdtuA)

## Prepatar o Ubuntu para instalação:

#### 1 – Atualizar o Ubuntu
```
sudo apt update
````
## Instalar e configurar o gerenciador de janelas:
#### 2 - Uma vez atualizado o sistema, vamos instalar o gerenciador de exibição Lightdm com o seguinte comando:
```
sudo apt install lightdm
```
#### 3 - Aceitar para continuar com o download e a instalação, então será exibido o menu:
![Imagem1](https://github.com/user-attachments/assets/403ca6f6-2855-47b1-a9f3-8181677765d5)
<br/>Selecionamos `lightdm` e continuamos a instalação. O objetivo do Lightdm é ser o padrão para o sistema de janelas **X11**;

#### 4 - Após isso reiniciamos o sistema para finalizar o processo, acessamos a tela de login, onde devemos selecionar **_Ubuntu on Xorg_**;
<br/>

![Imagem2](https://github.com/user-attachments/assets/a8ec3d3c-e457-49ea-819d-5f15784731dd)

![Imagem3](https://github.com/user-attachments/assets/08383002-2cbd-4b07-a577-ea84736f8b04)
<br/>
## Instalar e configurar o VNC:
#### 5 – Realizar a instalação do VNC com o seguinte comando:
```
sudo apt install x11vnc
````
#### 6 - Configurar o serviço do VNC, definir senha.
>Use o seguinte comando para criar o arquivo
````
sudo nano /lib/systemd/system/x11vnc.service
````
>Dentro do arquivo vamos colar esse texto e substituir a palavra **SUASENHAAQUI**, coloque sua senha de acesso do vnc.
````
[Unit]
Description=x11vnc service
After=display-manager.service network.target syslog.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -forever -display :0 -auth guess -passwd SUASENHAAQUI
ExecStop=/usr/bin/killall x11vnc
Restart=on-failure

[Install]
WantedBy=multi-user.target
````
Para salvar use o comando ```Ctrl + O```
<br/>
Para sair use o comando ```Ctrl + X```
<br/>
#### 7 – Devemos reiniciar os serviços com o comando:
````
systemctl daemon-reload
````
#### 8 – Habilitar o serviço do VNC
````
systemctl enable x11vnc.service
````
#### 9 – Iniciar o serviço do VNC
````
systemctl start x11vnc.service
````
#### 10 – Conferir o Status do VNC
````
systemctl status x11vnc.service
````
![Imagem4](https://github.com/user-attachments/assets/278d2938-5efc-40e3-a3bd-f82da0a9edc2)


#### Sucesso!

[]`s TiagoRFM

