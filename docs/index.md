# Practica 2.3

## Introduccion
 En esta practica vamos a configurar un servidor Proxy Inverso, primero clonamos la máquina de Debian donde tenemos, configurado nuestro servidor web de las prácticas anteriores, allí donde se configarará el Proxy que redigirirá cada petición que le llegue, al sevidor web configurado en la máquina original


## Reconfigurar el servidor web

### Primero cambiamos el nombre del archivo de configuracion del servidor web a webserver <br>


![01_cambiamos_elnombre_del_conf](assets/01_cambiamos_el_nombre_del_conf.png)


### Cambiamos el puerto en el archivo de conf a 8080:

![02_cambiar_conf_8080.png](assets/02_cambiar_conf_8080.png)


### Borramos el link simbolico antiguo:

![03_borrar_link_simbolico_antiguo.png](assets/03_borrar_link_simbolico_antiguo.png)


### Creamos uno nuevo:
![png](assets/04_crear_nuevo_link_simbolico.png)

### Reiniciamos nginx comprobando el sintaxis del conf antes:

![5_Nuevo_link](assets/05_verificarsin_restartmginx.png) <br>


### Configuramos el archivo de conf de Proxy
- El puerto: 80
- Y ponemos para que dirige la petición a nuestro servidor web ```webserver```
<br>

![png](assets/06_archiv_conf_proxy.png)

### Creammos un link simbolico a site-enabled para habilitar la configuracion

![png](assets/07_link_simbolico_proxy.png)


### Reiniciamos nginx:

![png](assets/08_restartnginx.png)


### Configuramos el **hosts** de la máquina anfitriona poniendole la ip de la máquina del proxy y el puerto 80 por defecto  


![png](assets/09_anadir_ip_proxy_hosts.png)

## **Cabezeras**

* Ahora ya al acceder a nuestro servidor a través del navegador nos salen las cabezeras, y apreciamos que Remote address tiene como ip, la del Proxy, lo que significa que todo funciona como debe de funcionar.

![png](assets/10_cabezeras.png)


### Cabecera Host en Proxy

* Vamos a ponerle una cabezera hosts a nuestro proxy que será ```Proxy_inverso_yahya```

![png](assets/11_cabezera_proxy.png)

                                     
### Cabezera Host en Webserver

* Hacemos lo mismo para el servidor web poniendole ```webserver``` 

![png](assets/12_cabezera_server.png)

###  Y ahora ya se ven las cabezeras ```Host``` de los 2 servidores [Proxy, Web]

![png](assets/13_cabezeras_chrome.png)
