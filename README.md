# KLIPPER > ANDROID

***NO ME HAGO RESPONSABLE DE NINGUN DAÑO O PERJUICIO QUE SE GENERE MEDIANTE EL ROOT, MALA INSTALACION O ACTUALIZACION DE FIRMWARE. HE PROBADO EN 3 DISPOSITIVOS DISTINTOS Y FUNCIONARON PERFECTAMENTE***

SE NECESITAN LAS SIGUIENTES HERRAMIENTAS:

-Contar con un celular root (tener habilitado el superusuario) aplicación Magisc para manejar root o algún otro programa de permisos root//// USUARIOS AVANZADOS

-Contar con un OTG (para conectar celular a impresora 3d)

-Cable USB con ficha según placa de impresora 3d

-Al finalizar la instalación de Klipper se puede generar el archivo (.bin), el cual hay que introducir en la impresora y encender para actualizar el firmware (no todas las impresoras son compatibles). 

¡¡¡Con klipper la pantalla de la impresora pueda quedar sin dar imagen porque usa la del celular para el menu. Si se vuelve a marlin el firmware estara operativa nuevamente!!! Se recomienda desconexión de display de mainboard

//// APLICACIONES PARA ANDROID ////

XServer-XSDL-1.20.51.apk, link: https://sourceforge.net/projects/libsdl-android/files/apk/XServer-XSDL/   
//// ES UN EMULADOR DE PANTALLA VIRTUAL DONDE SE CONECTA KLIPPER PARA MOSTRAR EL MENU ////

linuxdeploy-2.6.0-259.apk, link: https://github.com/meefik/linuxdeploy/releases/download/2.6.0/linuxdeploy-2.6.0-259.apk   
//// ES EL EMULADOR DE LINUX DONDE CORRE DEBIAN PARA INSTALAR KLIPPER ////

kerneladiutor_248.apk link: https://f-droid.org/en/packages/com.nhellfire.kerneladiutor/     
/// SIRVE PARA MEJORAR RENDIMIENTO ////

termux_118.apk SE INSTALA DE F-DROID O DEL PLAY STORE, link: https://github.com/termux/termux-app/releases/tag/v0.118.0  
///ES LA TERMINAL QUE SIRVE PARA AVERIGUAR MEDIANTE COMANDOS EL PUERTO AL QUE SE CONECTO OCTOPRINT CON LA IMPRESORA 3D MEDIANTE EL OTG

octo4a-1.2.5.apk link, https://github.com/feelfreelinux/octo4a/releases/download/1.2.5/octo4a-1.2.5.apk    
////SIRVE PARA USAR EL PUERTO OTG DEL CELULAR CON LA IMPRESORA Y USAR LA CAMARA PARA HACER TIMELAPSE O VERLA MEDIANTE LA WEB ////

/// APLICACIONES PARA WINDOWS ////

PUTTY link: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

WIN SCP link: https://winscp.net/eng/downloads.php

///DESCARGAR ARCHIVO MODIFICADO ///
link: 

- Abrir la aplicacion XSDL y presionar botón superior apenas inicia. Configurar mouse simulation / mouse simulation mode / desktop version, no simulation
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


-Abrir herramienta PUTTY desde windows para enviar comandos en ssh

/// USAR PUERTO IP QUE MUESTRA LA APLICACION LINUX DEPLOY PARA USAR EN PUTTY ///
-	Utilizar USUARIO: print3D CONTRASEÑA 123456

(Copiar siguientes comandos en orden con Control + C y en putty presionar click derecho para pegar) luego presionar ENTER

COMANDOS SSH:

1- sudo usermod -a -G aid_inet,aid_net_raw root

2- sudo apt update

3- sudo apt install -y git vim wget

4- cd ~

5- git clone https://github.com/th33xitus/kiauh.git

6- kiauh/kiauh.sh

![image](https://github.com/Tronix3d/Klipper-en-Android/assets/15800124/07550f04-0b3a-4aea-a4d4-48eb0b54af6f)


//////////////////////////////////////////////////////////
- OPCION 1 - ENTER
- INSTALAR KLIPPER CON - OPCION 1 - 1 - 1
- INSTALAR MOONRAKER - OPCION 2
- INSTALAR FLUIDD - OPCION 4
- INSTALAR KLIPPER SCREEN - OPCION 5
- PRESIONAR B - ENTER
- PRESIONAR Q - ENTER
- (MAS ADELANTE PODEMOS CREAR EL FIRMWARE PARA LA IMPRESORA (.BIN) EN LA OPCION 4 (ADVANCE), PERO CONVIENE SACAR INFORMACION DEL ARCHIVO CONFIG_EXAMPLES EN KLIPPER PARA CONFIGURAR EL PROCESADOR DE LA PLACA)
  
/////////////////////////////////////////////////////////

7- rm /home/print3D/printer_data/config/*

8- cd ~

9- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/fluidd.cfg

10- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/homing_override.cfg

11- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/moonraker.conf

12- sudo wget -P /home/print3D/printer_data/config/ https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/printer.cfg

13- cd ~

14- sudo wget https://raw.githubusercontent.com/gaifeng8864/klipper-on-android/main/configuration_klipper_family.sh

///////////////////////////////////////////////////////////////////////////////

- Abrir OCTOPRINT y conectar impresora al OTG mediante el USB
- Detener servicio de OCTOPRINT
- Abrir TERMUX y enviar siguientes comandos para saber el puerto donde está conectada la impresora

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

- Detener servicio en LINUX DEPLOY y luego ejecutarlo con start
- Colocar ip de LINUX DEPLOY en el navegador de windows
- usuario: print3d password: 123456
- Ir a la opcion de {...} configuracion del lado izquierdo
- Ir a CONFIG_EXAMPLES
- Buscar modelo de impresora 3d y abrir el archivo haciendo click
- Copiar el todo el contenido del archivo
- Cerrar archivo
- Abrir archivo PRINTER.CFG
- Borrar todo el contenido y pegar el que copiamos
- Buscar en el texto
  [mcu]
  serial: /dev/pts/0 ////CAMBIAR 0 POR PUERTO QUE CORRESPONDA DE TERMUX
- Reiniciar klipper
- Si no funciona detenemos LINUX DEPLOY y lo volvemos a iniciar

  

