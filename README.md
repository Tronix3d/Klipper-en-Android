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

Architecture (armhf) (revisar la arquitectura de tu celular, si soporta 64 bits, cambiar por arm64)

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

/////IR AL BOTON SUPERIOR DERECHO Y PRESIONAR INSTALAR, PARA QUE SE CARGUE DEBIAN EN LINUX DEPLOY.
UNA VEZ QUE TERMINA, PRESIONAR STOP Y PRESIONAR START ///


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

15- sudo nano configuration_klipper_family.sh

16 - seguir los siguientes pasos para editar archivo anterior

///////////////////////////////////////////////////////////////////////////////

- Abrir OCTOPRINT e instalarlo en android
- Una vez que termine la instalación conectar impresora al OTG mediante el USB
- Detener servicio de OCTOPRINT
- Abrir TERMUX y enviar siguientes comandos para saber el puerto donde está conectada la impresora

  1- pkg install tsu
  
  2- sudo ls -al /data/data/com.octo4a/files/serialpipe

  (entrega el puerto a donde debemos conectarnos /dev/pts/0) este puede variar
  
///////////////////////////////////////////////////////////////////////////////
 
17- reemplaza /dev/ttyACM0 por "/dev/pts/0" (Cambiar 0 por el numero que aroja termux al enviar comando (sudo ls -al /data/data/com.octo4a/files/serialpipe) )

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
- Si salen advertencias en amarillo modificar nuevamente archivo printer.cfg y agregar el siguiente codigo:
  
//////////////////////////////////////////////////////////////////


[virtual_sdcard]
path: /home/print3D/printer_data/gcodes

[display_status]

[pause_resume]

[gcode_macro PAUSE]
description: Pause the actual running print
rename_existing: PAUSE_BASE
# change this if you need more or less extrusion
variable_extrude: 1.0
gcode:
  ##### read E from pause macro #####
  {% set E = printer["gcode_macro PAUSE"].extrude|float %}
  ##### set park positon for x and y #####
  # default is your max posion from your printer.cfg
  {% set x_park = printer.toolhead.axis_maximum.x|float - 5.0 %}
  {% set y_park = printer.toolhead.axis_maximum.y|float - 5.0 %}
  ##### calculate save lift position #####
  {% set max_z = printer.toolhead.axis_maximum.z|float %}
  {% set act_z = printer.toolhead.position.z|float %}
  {% if act_z < (max_z - 2.0) %}
      {% set z_safe = 2.0 %}
  {% else %}
      {% set z_safe = max_z - act_z %}
  {% endif %}
  ##### end of definitions #####
  PAUSE_BASE
  G91
  {% if printer.extruder.can_extrude|lower == 'true' %}
    G1 E-{E} F2100
  {% else %}
    {action_respond_info("Extruder not hot enough")}
  {% endif %}
  {% if "xyz" in printer.toolhead.homed_axes %}
    G1 Z{z_safe} F900
    G90
    G1 X{x_park} Y{y_park} F6000
  {% else %}
    {action_respond_info("Printer not homed")}
  {% endif %} 

[gcode_macro RESUME]
description: Resume the actual running print
rename_existing: RESUME_BASE
gcode:
  ##### read E from pause macro #####
  {% set E = printer["gcode_macro PAUSE"].extrude|float %}
  #### get VELOCITY parameter if specified ####
  {% if 'VELOCITY' in params|upper %}
    {% set get_params = ('VELOCITY=' + params.VELOCITY)  %}
  {%else %}
    {% set get_params = "" %}
  {% endif %}
  ##### end of definitions #####
  {% if printer.extruder.can_extrude|lower == 'true' %}
    G91
    G1 E{E} F2100
  {% else %}
    {action_respond_info("Extruder not hot enough")}
  {% endif %}  
  RESUME_BASE {get_params}

[gcode_macro CANCEL_PRINT]
description: Cancel the actual running print
rename_existing: CANCEL_PRINT_BASE
gcode:
  TURN_OFF_HEATERS
  CANCEL_PRINT_BASE


/////////////////////////////////////////////////

20- VER PARTE SUPERIOR DE ARCHIVO CONFIG.CFG Y SACAR INFORMACION DE MICROCONTROLADOR PARA PODER CREAR ARCHIVO .BIN PARA ACTUALIZAR FIRMWARE DE IMPRESORA 3D
21- EN LA CONSOLA DE PUTTY ENVIAR NUEVAMENTE LO SIGUIENTE
22- kiauh/kiauh.sh

![image](https://github.com/Tronix3d/Klipper-en-Android/assets/15800124/d31847a0-36c0-4dc8-a012-e2edd5c71098)

23- OPCION 4

24- OPCION 2

![image](https://github.com/Tronix3d/Klipper-en-Android/assets/15800124/6442a93d-324d-4312-a1ae-a7c65dc15e59)

25- CONFIGURAR PARAMETROS CON LOS DATOS EXTRAIDOS DE CONFIG.CFG

![image](https://github.com/Tronix3d/Klipper-en-Android/assets/15800124/4485b55a-b110-4ec1-a0c9-4f322884b232)

26- PRESIONAR Q - ENTER Y GUARDAR CON Y (ESTO GENERA UN ARCHIVO .BIN PARA GUARDAR EN LA MICRO SD)
27- ABRIR PROGRAMA WIN SCP EN WINDOWS Y COPIAR EL ARCHIVO DE LA CARPETA KLIPPER/OUT/KLIPPER.BIN 




  

