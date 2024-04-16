---
description: >-
  En esta sección aprenderemos cómo configurar un servidor nginx multidominio y
  veremos aplicaciones del uso de proxies.
---

# UF3 Servidor web y servidor proxy.

## WEB.

En esta sección trataremos de responder a algunas preguntas básicas sobre la red de redes.

### Definición de web.

### Definición de HTTP.

### Arquitectura en el intercambio  de mensajes.

FUENTES:

RFC de HTTP/3: [https://www.rfc-editor.org/rfc/rfc9412.html](https://www.rfc-editor.org/rfc/rfc9412.html)

HTTP según IONOS: [https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/protocolo-http/](https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/protocolo-http/)

## PROXYS.

En esta sección definiremos qué es un proxy, cuáles son sus principales aplicaciones y su comparativa con una red provada virtual o VPN.

### Definición de proxy.

Servidor intermediario entre el cliente y el servidor al que se pretende acceder. En este tipo de conexiones se da la particularidad de que el servidor al que finalmente accedemos sólo ve la IP del intermediario.&#x20;

### Cuatro finalidades del proxy.

Podemos distinguir cuatro aplicaciones interesantes de los proxys:

* Ocultación de la propia IP.
* Evitación de bloqueos geográficos.&#x20;
* Servir un contenido estático de un servidor web gracias al almacenamiento en una caché. Exponer la IP del proxy y no la IP del servidor principal conlleva un aumento de la seguridad por la ofuscación de IP.&#x20;
* Filtrar contenido, bloquear sitios maliciosos, podemos filtrar los sitios inadecuados para ciertas audiencias, como menores.

### Proxy vs VPN.

Proxy: cifro... tráfico web.&#x20;

VPN: cifro... todo el tráfico.&#x20;

Por tanto la seguridad en una VPN es ...SUPERIOR... que en un proxy.&#x20;

La velocidad de un proxy es más ...LENTA... que una VPN.



FUENTES:

{% embed url="https://www.redeszone.net/tutoriales/redes-cable/que-es-servidor-proxy-configurar/" %}

