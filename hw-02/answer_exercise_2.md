# Ejercicio 2
   
##  Crear un objeto de tipo replicaSet a partir del objeto anterior con las siguientes especificaciones:
### Debe tener 3 replicas
Ejecutamos el comando:
`kubectl apply -f nginx-replicaser.yaml`
Vemos los replicaset:
`kubectl get rs`

### ¿Cúal sería el comando que utilizarías para escalar el número de replicas a 10?
`kubectl scale --replicas=10 rs my-nginx`
### Si necesito tener una replica en cada uno de los nodos de Kubernetes, ¿qué objeto se adaptaría mejor? (No es necesario adjuntar el objeto)

El objeto que mejor se adaptaria seria un DaemonSet, debido a que es el que garantiza que todos (o algunos) de los nodos ejecuten una copia de un Pod. 


