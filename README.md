# ARPRINT3D
KLIPPER > ANDROID

***NO ME HAGO RESPONSABLE DE NINGUN DAÑO O PERJUICIO QUE SE GENERE MEDIANTE EL ROOT, MALA INSTALACION O ACTUALIZACION DE FIRMWARE. HE PROBADO EN 3 DISPOSITIVOS DISTINTOS Y FUNCIONARON PERFECTAMENTE***

NECESITAMOS LAS SIGUIENTES HERRAMIENTAS:

-CONTAR CON UN CELULAR ROOT(TENER HABILITADO EL SUPERUSUARIO) APLICACIÓN MAGISC PARA MANEJAR ROOT O ALGUN OTRO PROGRAMA DE PERMISOS ROOT//// USUARIOS AVANZADOS

-CONTAR CON UN OTG (PARA CONECTAR CELULAR A IMPRESORA 3D)

-CABLE USB CON FICHA SEGUN PLACA DE IMPRESORA 3D

-UNA VEZ INSTALADO KLIPPER SE PUEDE GENERAR EL ARCHIVO .BIN DESDE KIAUH EL CUAL HAY QUE INTRODUCIR EN LA IMPRESORA Y ENCENDER PARA ACTUALIZAR EL FIRMWARE (NO TODAS LAS IMPRESORAS SON COMPATIBLES). 

¡¡¡CON KLIPPER LA PANTALLA DE LA IMPRESORA PUEDA QUEDAR SIN DAR IMAGEN PORQUE USA LA DEL CELULAR PARA EL MENU. SI SE VUELVE A MARLIN ESTARA OPERATIVA NUEVAMENTE!!!

//// APLICACIONES PARA ANDROID ////

XServer-XSDL-1.20.51.apk, link: https://sourceforge.net/projects/libsdl-android/files/apk/XServer-XSDL/   
//// ES UN EMULADOR DE PANTALLA VIRTUAL DONDE SE CONECTA KLIPPER PARA MOSTRAR EL MENU ////

linuxdeploy-2.6.0-259.apk, link: https://github.com/meefik/linuxdeploy/releases/download/2.6.0/linuxdeploy-2.6.0-259.apk   
//// ES EL EMULADOR DE LINUX DONDE CORRE DEBIAN PARA INSTALAR KLIPPER ////

kerneladiutor_248.apk link: https://f-droid.org/en/packages/com.nhellfire.kerneladiutor/     
/// SIRVE PARA MEJORAR RENDIMIENTO ////

termux_118.apk SE INSTALA DE F-DROID O DEL PLAY STORE, link: https://github.com/termux/termux-app/releases/tag/v0.118.0  
///ES LA TERMINAL QUE SIRVE MEDIANTE COMANDOS PARA AVERIGUAR EL PUERTO AL QUE SE CONECTO OCTOPRINT CON LA IMPRESORA 3D MEDIANTE EL OTG

octo4a-1.2.5.apk link, https://github.com/feelfreelinux/octo4a/releases/download/1.2.5/octo4a-1.2.5.apk    
////SIRVE PARA USAR EL PUERTO OTG DEL CELULAR CON LA IMPRESORA Y USAR LA CAMARA PARA HACER TIMELAPSE O VERLA MEDIANTE LA WEB ////

/// APLICACIONES PARA WINDOWS ////

PUTTY link: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

WIN SCP link: https://winscp.net/eng/downloads.php

///DESCARGAR ARCHIVO MODIFICADO ///
link: 

- ABRIR LA APLICACION XSDL Y PRESIONAR BOTON SUPERIOR APENAS INICIA CONFIGURAR Mouse Simulation / Mouse Simulation Mode / Desktop version, no simulation
- ABRIR LINUX DEPLOY Y CONFIGURAR PROGRAMA ![image](https://github.com/Tronix3d/ARPRINT3D/assets/15800124/4eb011d2-9bb0-4b8b-af16-4a8d1c1d0766)

Lock screen (no)

Lock Wi-Fi (yes)

Wake lock (yes)

Autostart (yes)

Autostart delay (5)

Track network changes (yes)

Las demas opciones en default

- LUEGO CONFIGURAR DEBIAN CON LAS SIGUIENTES PROPIEDADES ![image](https://github.com/Tronix3d/ARPRINT3D/assets/15800124/f669e6ca-69b7-4564-8640-640ff72454be)

Distribution (Debian)

Architecture (armhf) (revisar la arquitectura de tu celular, si soporta 64 bits, cambiar por arm64

Distribution suite (oldstable)

Installation type (Directory)

Installation path   /data/debian

Username (print3D) respetar este usuario para los siguientes comandos

User password: (123456) respetar o mofificar en caso de que haga falta ////ESTO SE USAR PARA INGRESAR POR SSH O WEB

INIT (enable)

Init system (sysV)

SSH (enabled)

GUI (enabled)

Graphics subsystem (X11)

Desktop environment (XTerm)


-ABRIR HERRAMIENTA PUTTY DESDE WINDOWS PARA ENVIAR COMANDOS EN SSH

/// USAR PUERTO IP QUE MUESTRA LA APLICACION LINUX DEPLOY PARA USAR EN PUTTY ///
USAR USUARIO: print3D CONTRASEÑA 123456

(Copiar siguientes comandos en orden con Control + C y en putty presionar click derecho para pegar) luego presionar ENTER

COMANDOS SSH:

1- sudo usermod -a -G aid_inet,aid_net_raw root

2- sudo apt update

3- sudo apt install -y git vim wget

4- cd ~

5- git clone https://github.com/th33xitus/kiauh.git

6- kiauh/kiauh.sh

7- rm /home/print3D/printer_data/config/*

8- cd ~

9- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/fluidd.cfg

10- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/homing_override.cfg

11- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/moonraker.conf

12- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/printer.cfg

13- cd ~

14- sudo wget https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/configuration_klipper_family.sh

///////////////////////////////////////////////////////////////////////////////

- ABRIR OCTOPRINT Y CONECTAR IMPRESORA AL OTG MEDIANTE EL USB
- FRENAR SERVICIO DE OCTOPRINT
- ABRIR TERMUX Y ENVIAR SIGUIENTE COMANDOS PARA SABER EL PUERTO DONDE ESTA CONECTADA LA IMPRESORA

  1- pkg install tsu
  
  2- sudo ls -al /data/data/com.octo4a/files/serialpipe
  
///////////////////////////////////////////////////////////////////////////////

- DESACARGAR ARCHIVO DE REPOSITORIO Y REEMPLAZAR configuration_klipper_family.sh CON WIN SCP   (SINO EJECUTAR LOS PASOS 15, 16 , 17, 18, 19)

/////////////////////////////////////////////////////////////////////////////////

15- sudo nano configuration_klipper_family.sh

16- modificar "/dev/pts/0" (Cambiar 0 por el numero que aroja termux al enviar comando (sudo ls -al /data/data/com.octo4a/files/serialpipe) )

17-modificar chmod 777 /dev/pts/0  (Cambiar 0 por el numero que aroja termux al enviar comando (sudo ls -al /data/data/com.octo4a/files/serialpipe) )

18- salir con CONTROL+X, guardar archivo YES y sobreescribir presionando ENTER

19- bash configuration_klipper_family.sh

- PARAR SERVICIO EN LINUX DEPLOY Y LUEGO EJECUTARLO CON START
- COLOCAR IP DE LINUX DEPLOY EN EL NAVEGADOR DE WINDOWS
- USUARIO: print3D PASSWORD: 123456
- IR A LA OPCION DE {...} CONFIGURACION DEL LADO IZQUIERDO
- IR A CONFIG_EXAMPLES
- BUSCAR MODELO DE IMPRESORA 3D Y ABRIR EL ARCHIVO HACIENDO CLICK
- COPIAR EL TODO EL CONTENIDO DEL ARCHIVO
- CERRAR ARCHIVO
- ABRIR ARCHIVO PRINTER.CFG
- BORRAR TODO EL CONTENIDO Y PEGAR EL QUE COPIAMOS
- BUSCAR EN EL TEXTO
  [mcu]
  serial: /dev/pts/0 ////CAMBIAR 0 POR PUERTO QUE CORRESPONDA DE TERMUX
- REINICIAR KLIPPER
- SINO FUNCIONA DETENEMOS LINUX DEPLOY Y LO VOLVEMOS A INICIAR
  

