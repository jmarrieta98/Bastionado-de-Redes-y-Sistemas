author: Jose Manuel Arrieta
summary: Hardening BIOS Lenovo Ideapad Slim 9 14ITL5
id: lenovo
categories: codelab,markdown,hardening,bios
environments: Web
status: Published

# Bastionado del arranque del sistema de Lenovo Ideapad Slim 9 14ITL5
## Inicio
Para acceder a la BIOS tendremos presionar el botón F2 a la hora de iniciar el sistema.
## Contraseña de usuario o Power-On
Si queremos que al iniciar el sistema este nos pida una contraseña para acceder, tendremos que ir a la pestaña **Security** de la BIOS y en la opción **Set Hard Disk Password** nos pedirá escribir una contraseña.
![Contraseña de usuario](lenovo/img/user_password.png)

## Contraseña de administrador
Si queremos que al acceder a la BIOS nos pida una contraseña, tendremos que acceder a la pestaña **Security** y en la opción **Set Administrator Password** nos pedirá escribir una contraseña.
![Contraseña de administrador](lenovo/img/administrator_password.png)
## Arranques externos
Para deshabilitar el arranque externo, en la pestaña **BOOT** y en **USB BOOT** podemos bloquear los usb para que no puedan arrancar desde ellos.
![Seguridad USB](lenovo/img/usb_security.png)

## Orden de arranque
Para cambiar el orden de arranque tan solo tendremos que entrar en la pestaña **Boot** y en el apartado **EFI** podemos elegir que dispositivo arranca primero
![Orden de arranque](lenovo/img/boot_priorities.png)

## Otras opciones de seguridad
Dentro de **Security** tenemos la opción **Secure Boot menu** que podemos habilitarla.
![Bloquear interfaces varias](lenovo/img/secure_boot.png)
También dentro de **Boot** y en **PXE Boot to LAN** podemos bloquear la interfaz de red.
![Bloquear LAN](lenovo/img/other_secure.png)