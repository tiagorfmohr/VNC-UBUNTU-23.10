# Como Instalar o VNC no UBUNTU 23.10

Neste passo a passo você irá aprender como realizar a instalação e configuração do acerro remoto através do VNC.

## Prepatar o Ubuntu para instalação:

1 – Atualizar o Ubuntu
```
sudo apt update
````
2 - Uma vez atualizado o sistema, vamos instalar o gerenciador de exibição Lightdm com o seguinte comando:
```
sudo apt install lightdm
```
3 - Aceitar para continuar com o download e a instalação, então será exibido o menu:
Selecionamos “lightdm” e continuamos a instalação. O objetivo do Lightdm é ser o padrão para o sistema de janelas X11

4 - Após isso reiniciamos o sistema para finalizar o processo, acessamos a tela de login, onde devemos selecionar Ubuntu on Xorg;
5 – Abrir o terminar e executar o seguinte comando
sudo apt install x11vnc
6- Listamos o IP do Ubuntu 20.04 com o comando:
ip add
depois
x11vnc
7- Agora para configurar o serviço do VNC, definir senha.
Seguinte comando para criar o arquivo
sudo nano /lib/systemd/system/x11vnc.service

Dentro do arquivo vamos colar esse texto e onde tem a palavra SUASENHAAQUI, coloque a senha de acesso do vnc

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

Para salvar use o comando Ctrl + O
Para sair use o comando Ctrl + X
8 – Devemos reiniciar os serviços com o comando:
systemctl daemon-reload
9 – Habilitar o serviço do VNC
systemctl enable x11vnc.service
10 – Iniciar o serviço do VNC
systemctl start x11vnc.service
11 – Conferir o Status do VNC
systemctl status x11vnc.service
 

