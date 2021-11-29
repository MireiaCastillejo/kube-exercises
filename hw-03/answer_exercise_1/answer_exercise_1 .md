# Ejercicio 1 
   
 ## [Ingress Controller / Secrets] Crea los siguientes objetos de forma declarativa con las siguientes especificaciones:
• Imagen: nginx
• Version: 1.19.4
• 3 replicas
• Label: app: nginx-server
• Exponer el puerto 80 de los pods
• Limits: CPU: 20 milicores 
          Memoria: 128Mi
• Requests: CPU: 20 milicores 
            Memoria: 128Mi



Se necesita habilitar ingress en minikube para el uso de Ingress:
```
minikube addons enable ingress
````
## Apartado a:

Creamos los objetos:

```

  kubectl create -f deployment.yaml

  kubectl create -f service.yaml

  kubectl create -f ingress.yaml

  kubectl get all

  kubectl get ingress

```

Configuramos el archivo host añadiendo mireia.student.lasalle.com
Ejecutamos el comando:

``` minikube tunnel```


Verificar que el controlador de Ingress esta dirigiendo el tráfico a la URL:
http://mireia.student.lasalle.com

## Apartado b:
Generamos un certificado:

```shell script
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout key.pem -out cert.pem -subj "/CN=mireia.student.lasalle.com/O=mireia.student.lasalle.com"
```

Y creamos un `Secret` con los certificados:

```shell script
kubectl create secret tls secret-tls --key key.pem --cert cert.pem
```
Ejecutamos el comando

``` minikube tunnel```

Accedemos a la página
<img width="766" alt="Captura de pantalla 2021-11-29 a las 11 42 07" src="https://user-images.githubusercontent.com/26769446/143856796-263db8ba-4c54-4a1a-ae13-5755350e86d2.png">
