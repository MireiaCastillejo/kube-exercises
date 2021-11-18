# Ejercicio 1 
   
 ## ¿Cómo puedo obtener las últimas 10 líneas de la salida estándar (logs generados por la aplicación)?
 `k logs -f --tail 10 my-nginx`
 ## ¿Cómo podría obtener la IP interna del pod? Aporta capturas para indicar el proceso que seguirías.
 `kubectl get pod -o wide`
 ## ¿Qué comando utilizarías para entrar dentro del pod?
 `kubectl exec --stdin --tty my-nginx -- /bin/bash`
 ## Necesitas visualizar el contenido que expone NGINX, ¿qué acciones debes llevar a cabo?
Vemos en el puerto que esta mostrando y vamos a la dirección que nos marca.
    `kubectl port-forward nginx 8080:80`
Tambien podemos acceder dentro con el comando
     `kubectl exec --stdin --tty my-nginx -- /bin/bash`
Y accedemos a la carpeta donde contiene el html que es lo que expone: haciendo 
`cd /usr/share/nginx/html`
Accedemos dentro del html `cat index.html`

 ## Indica la calidad de servicio (QoS) establecida en el pod que acabas de crear. ¿Qué lo has mirado?
 Ejecutamos el comando:
    `kubectl get pod nginx --output=yaml`
