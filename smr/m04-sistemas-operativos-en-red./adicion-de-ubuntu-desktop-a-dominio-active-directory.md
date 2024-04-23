---
description: >-
  Entre las operaciones de sistemas heterogéneos, una de las que suelen resultar
  más complejas a mis alumnos es la de la adición de una máquina Ubuntu
  declarada como equipo en una estructura de AD.
---

# Adición de Ubuntu Desktop a dominio Active Directory



Partimos de la structura de Active Directory de la ilustración.

<figure><img src="../.gitbook/assets/ad_atlantica_local.png" alt=""><figcaption><p>Detalle de la organización ficticia de Atláántica Shipping Company.</p></figcaption></figure>

Nos fijamos en el nombre completo que debe tener la máquina conta01: conta01.atlantica.local.

Configuramos /etc/hosts.

Configuramos /etc/hostname.

```
conta01.atlantica.local
```

Configuramos /etc/resolv.conf. En el search debe aparecer el dominio del bosque y la IP del AD como DNS.

Instalamos los paquetes necesarios para agregar la máquina Ubuntu Desktop al dominio.&#x20;

```bash
$ sudo apt install realmd sssd oddjob oddjob-mkhomedir adcli samba-common
```

(Ver capturas)

Es necesario cambiar en /etc/sssd/sssd.conf la línea use\_fullt\_qualified\_names a False
