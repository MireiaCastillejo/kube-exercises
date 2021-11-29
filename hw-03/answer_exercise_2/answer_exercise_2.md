# Ejercicio 2
   
## [StatefulSet] Crear un StatefulSet con 3 instancias de MongoDB (ejemplo visto en clase)
### Se pide:
### • Habilitar el clúster de MongoDB
### • Realizar una operación en una de las instancias a nivel de configuración y verificar que el cambio se ha aplicado al resto de instancias
### • Diferencias que existiría si el montaje se hubiera realizado con el objeto de ReplicaSet


Ejecutamos las siguientes instrucciones:

``kubectl apply -f service.yaml``

``kubectl apply -f statefulset.yaml``

Ingresamos a el pod mongod-0 para habilitar el cluster de mongoDB

`` kubectl exec -it mongod-0 -- bash``

``mongosh --quiet``

``` 
rs.initiate({ _id: "rs0", version: 1, members: [ 
 { _id: 0, host: "mongo-0.mongo-svc.default.svc.cluster.local:27017" }, 
 { _id: 1, host: "mongo-1.mongo-svc.default.svc.cluster.local:27017" }, 
 { _id: 2, host: "mongo-2.mongo-svc.default.svc.cluster.local:27017" } 
]});
Vemos la basededatos
    show dbs
Creamos una nueva:
    use basededatos
Insertamos datos:
    db.basededatos.insertOne({name: "Mireia", age: 26}))

A continuación vemos el cambio creado  
db.getMongo().setReadPref("secondary")
show dbs
use basededatos
show tables
db.basededatos.find()
```
Aqui podemos ver los cambios que se han añadido al pod
<img width="715" alt="Captura de pantalla 2021-11-29 a las 12 14 45" src="https://user-images.githubusercontent.com/26769446/143860432-bce0ca37-07cf-4fee-a44f-a15142d77a88.png">

## Diferencias que existiría si el montaje se hubiera realizado con el objeto de ReplicaSet

La diferencia que existiría si el montaje se hubiese realizado con el objeto ReplicaSet: es que si muere la instancia y el servicio vuelve a crear una nueva lo identificaria con un identificador diferente, de tal forma que perderiamos el estado de la replica anterior.
En cambio con el objeto StatefulSet, se vuelve a crear un nuevo pod con el mismo identificador que tenia asignado anteriormente.





