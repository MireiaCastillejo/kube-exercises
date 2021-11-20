# Ejercicio 2
   
##  Crear un objeto de tipo replicaSet a partir del objeto anterior con las siguientes especificaciones:
### Debe tener 3 replicas
Ejecutamos el comando:
`kubectl apply -f nginx-replicaser.yaml`
Vemos los replicaset:
`kubectl get rs`

### ¿Cúal sería el comando que utilizarías para escalar el número de replicas a 10?
`kubectl scale --replicas=10 rs my-nginx-replicaset`
<img width="762" alt="Captura de pantalla 2021-11-20 a las 13 07 00" src="https://user-images.githubusercontent.com/26769446/142725721-e21fed8a-449d-4c0b-8ab2-c8b8dc5e06cb.png">

### Si necesito tener una replica en cada uno de los nodos de Kubernetes, ¿qué objeto se adaptaría mejor? (No es necesario adjuntar el objeto)

El objeto que mejor se adaptaria seria un DaemonSet, debido a que es el que garantiza que todos (o algunos) de los nodos ejecuten una copia de un Pod. 


