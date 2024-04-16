---
description: >-
  Al principio expondré las condicones concretas de la máquina de trabajo,
  indicaré qué paquetes del repositorio instalar y finalizaré con la
  configuración del servidor samba.
---

# Despliegue de samba en Ubuntu Server.

## Compartir una carpeta en red desde un Ubuntu Server para ser accedida por red.&#x20;

Partimos de una distribución recién instalada de Ubuntu Server.

El detalle de la versión instalada puede apreciarse en la siguiente captura.

```shell
lsb_release -a
```

<figure><img src="../.gitbook/assets/Captura de pantalla 2024-02-13 a las 16.27.44.png" alt="" width="315"><figcaption><p>Versióón de referencia que utilizaremos en la configuración del servidor Samba.</p></figcaption></figure>

Durante este ejemplo se asume que somos el usuario ubuntu, y que estamos en nuestro directorio home.

```sh
whoami
pwd
```

<figure><img src="../.gitbook/assets/Captura de pantalla 2024-02-13 a las 16.52.54.png" alt="" width="236"><figcaption><p>Detalle del entorno desde el que realizaremos la configuración del servidor Samba.</p></figcaption></figure>

Debemos compartir LAN con un equipo que cuente con un cliente SMB. Averiguamos la configuración de red del servidor y comprobamos que tenemos acceso a internet.&#x20;

```sh
ip a
```

<figure><img src="../.gitbook/assets/Captura de pantalla 2024-02-13 a las 17.08.06.png" alt=""><figcaption><p>Detalle de la configuración IP.</p></figcaption></figure>

En este ejemplo la interfaz de nuestro interés es la enp0s3, lo que significa que nuestra direción IP es la 192.168.40.130.

Instalamos la implementación libre del servidor de protocolo SMB samba.



```sh
sudo apt -y install samba
```



Es necesario habilitar las reglas en el firewall para que se permitan las conexiones entrantes al protocolo SMB o CIFS.

```sh
sudo ufw enable
sudo ufw allow samba
sudo ufw status verbose
```

<figure><img src="../.gitbook/assets/Captura de pantalla 2024-02-13 a las 16.47.31.png" alt=""><figcaption><p>Detalle de las operaciones con el firewall.</p></figcaption></figure>

Creamos el directorio cuyo contenido compartiremos por red.

```sh
mkdir lectura_escritura
ls -l
```

<figure><img src="../.gitbook/assets/Captura de pantalla 2024-02-13 a las 17.22.40.png" alt=""><figcaption><p>Contenido de la carpeta home del usuario ubuntu.</p></figcaption></figure>

Añadimos al usuario ubuntu, para que pueda acceder al servicio samba.

```sh
sudo smbpasswd -a ubuntu
```

Hemos de realizar la configuración del servicio modificando el fichero /etc/samba/smb.conf. Para prevenir problemas copiamos el fichero original de configuración en nuestro directorio home. Esta práctica especialmente útil cuando se trata de nuestro primer contacto con un servidor.

```sh
cp /etc/samba/smb.conf ~
```

Ahora hemos de editar la configuración del servidor samba como administrador y definimos una nueva entrada al final, llamada lectura\_escritura, tal y como se aprecia en la captura.

```sh
sudo nano /etc/samba/smb.conf
```



<figure><img src="../.gitbook/assets/Captura de pantalla 2024-02-14 a las 9.33.37.png" alt=""><figcaption></figcaption></figure>

A efectos didácticos, muestro la diferencia del fichero original con el modificado.

```
diff /etc/samba/smb.conf ~/smb.conf
```

<figure><img src="../.gitbook/assets/Captura de pantalla 2024-02-14 a las 12.31.11 (1).png" alt=""><figcaption></figcaption></figure>

Reiniciamos el servicio de samba.

```sh
sudo service smbd restart
```

