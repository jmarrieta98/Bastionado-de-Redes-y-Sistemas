author: Jose Manuel Arrieta
summary: Protocolo de enrutamiento reguro
id: PES
categories: codelab,markdown,hardening,networks
environments: Web
status: Published

# Protocolo de enrutamiento seguro
## Inicio
Para empezar vamos a mostrar el suspuesto caso que vamos a realizar y a traves de esta guía y luego el ejercicio correspondiente, conseguiremos proteger una red con el protocolo OSPFv2.
El caso es el siguiente, hay **4** departamentos que deben estar conectados entre si, para eso cada departamento tiene una **red propia** y mediante el protocolo **OSPF** se comunicaran con los demás departamentos.
![Imagen del ejercicio](img/ejercicio.jpg) 
## IP estática en PCs
Antes de poner una ip estática a cualquier pc tendremos que tener en cuenta que la **primera ip** de la red de cada departamento será para el **router** y a partir de ahí podremos asignar las ip restantes a los pcs que tengamos.
Para asignar una ip al pc tendremos que clicar sobre el y este abrirá una ventana, clicaremos en la pestaña **desktop -> IP Configuration** y en el apartado IP Congfiguration elegimos la opción Static e introducimos la ip correspondiente e nuestro caso sera **192.168.X.X**
y la marcara de red que será **255.255.255.0**, la puerta por defecto será el router por lo que la ip será **192.168.X.1**
![Contraseña de usuario](img/pc.jpg)
## Entrar al modo configuración de un router
Para entrar en la consola del router deberemos de clicar en el y luego en la pestaña **CLI** se abrirá la terminal.
Para entrar en modo administrador deberemos de introducir **en** y luego para la configuracion **conf t** a partir de aquí podremos configurar el router.
![Modo configuración cisco](img/configuracion_router.jpg)

## Asignar IPs a los puertos
Una vez dentro del modo configuración para acceder a un puerto y darle una IP debremos de hacer lo siguiente introduciremos el siguiente comando **interface (NombreDelPuerto)** en el caso del puerto hacia el departamento sera **gigabitEthernet0/0/0** y para la comunicación entre departamentos **gigabitEthernet0/0/1**, luego para asignar la ip usaremos el siguiente comando **ip add (IP)192.168.X.1 (Máscara)255.255.255.0**
Para salir de una interfaz o simplemente ir hacia atras usaremos el comando **exit** y además debemos de activar el puerto porque por defecto está apagado, con **no sh** el puerto se encenderá.

## Protocolo OSPF (Identificación)
Para acceder al protocolo ospf tendremos que ir al modo configuración del router (Descrito anteriormente en las diapositivas) y usaremos el comando **router ospf id** (En este caso puede ser 1)
Para que no haya confusiones vamos a darle una id especifica al router para el protocolo ospf, para ello deberemos de escribir el siguiente comando dentro de la configuracion ospf **router-id X.X.X.X** Para entenderlo mejor usaremos el tercer octeto de la red del departamento para asignarle un id por ejemplo **1.1.1.1**

## Protocolo OSPF (Configuración)
Una vez dentro de la configuración de ospf debemos de añadir las redes de cada router a un area, en nuestro caso seran al backbone (0 o 0.0.0.0) con el siguiente comando **network 192.168.X.0 0.0.0.255(Máscara inversa) area 0**
Una vez añadamos todas las redes de los routers ya estará configurado.

## Protocolo OSPF (Enrutamiento)
Para ver si está correcto debemos de entrar en modo administrador en un router y escribir el siguiente comando **show ip ospf neighbor** y **show ip route**, con dichos comandos veremos los vecinos del router y las rutas que se han puesto gracias al protocolo ospf.
![Validar OSPF](img/ospf.jpg) 
## Protocolo OSPF (Securización)
Para activar la securización del protocolo ospf, deberemos de entrar en las interfaces que hayamos añadido y meter el comando **ip ospf message-disgest-key 1 mdr (Contraseña)**
y para activar la autenticación **ip ospf authentication message-digest**
Con esto habremos securizado la red y para comprobrar que todo está bien podemos hacer el paso anterior para ver que lo vecinos y las rutas son correctas.
## Práctica OSPF
En el siguiente enlace tendras el ejercicio para poder hacerlo en Cisco Packet Tracer.
[Ejercicio OSPf]()