EXERCISE 3
==========
# [Horizontal Pod Autoscaler] Crea un objeto de kubernetes HPA, que escale a partir de las métricas CPU o memoria (a vuestra elección). Establece el umbral al 50% de CPU/memoria utilizada, cuando pase el umbral, automáticamente se deberá escalar al doble de replicas.

Habilitamos el addon metrics-server para que el HPA pueda ver el uso de la CPU
``` minikube addons enable metrics-server```

Seguidamente creamos los objetos
```` kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml`
````
A continuación se realiza el autoscaling con el siguiente comando 
```kubectl autoscale deployment nginx-server --cpu-percent=50 --min=3 --max=6```

Verificamos el escalado:
``` kubectl get hpa```

Por último verificamso que al superar el 50% de limite de cpu se estan creando las replicas necesarias:
```` kubectl get hpa -w kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://nginx-svc; done"````

Para poder ver el autoescalado en directo ejecutamos en otra ventana el siguiente comando:
``` kubectl get hpa --watch```
