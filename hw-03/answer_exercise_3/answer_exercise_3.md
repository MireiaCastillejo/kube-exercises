EXERCISE 3
==========
## [Horizontal Pod Autoscaler] Crea un objeto de kubernetes HPA, que escale a partir de las métricas CPU o memoria (a vuestra elección). Establece el umbral al 50% de CPU/memoria utilizada, cuando pase el umbral, automáticamente se deberá escalar al doble de replicas.

Habilitamos el addon metrics-server para que el HPA pueda ver el uso de la CPU <br /> 
``` minikube addons enable metrics-server``` <br /> 

Seguidamente creamos los objetos<br /> 
```` kubectl apply -f deployment.yaml ````<br /> 
```` kubectl apply -f service.yaml ````<br /> 
A continuación se realiza el autoscaling con el siguiente comando <br /> 
```kubectl autoscale deployment nginx-server --cpu-percent=50 --min=3 --max=6```<br /> 

Verificamos el escalado:<br /> 
``` kubectl get hpa```<br /> 

Por último verificamos que al superar el 50% de limite de cpu se estan creando las replicas necesarias:<br /> 
````
kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://nginx-svc; done"
````
Para poder ver el autoescalado en directo ejecutamos en otra ventana el siguiente comando:<br /> 
``` kubectl get hpa --watch```<br /> 

<img width="965" alt="Captura de pantalla 2021-11-29 a las 14 05 53" src="https://user-images.githubusercontent.com/26769446/143876104-9afed335-c233-41c8-9941-4f0571ec5f9a.png"> <br /> 
Vemos el autoescalado de pods
<img width="965" alt="Captura de pantalla 2021-11-29 a las 14 06 18" src="https://user-images.githubusercontent.com/26769446/143876120-20b958a9-c65b-4738-9d35-b3dc563f2f94.png">
