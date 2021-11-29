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

``` minikube tunnel```


Verificar que el controlador de Ingress esta dirigiendo el tráfico a la URL:
http://mireila.student.lasalle.com

## Apartado b:

