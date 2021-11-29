# Ejercicio 2
   
## [StatefulSet] Crear un StatefulSet con 3 instancias de MongoDB (ejemplo visto en clase)
## Se pide:
## • Habilitar el clúster de MongoDB
## • Realizar una operación en una de las instancias a nivel de configuración y verificar que el cambio se ha aplicado al resto de instancias
## • Diferencias que existiría si el montaje se hubiera realizado con el objeto de ReplicaSet


Ejecutamos las siguientes instrucciones:

``kubectl apply -f service.yaml``

``kubectl apply -f statefulset.yaml``

se usa cuando se quiere persistir volumenes y se usa para garantizar que puedan mantener el estado en los reinicios de los componentes
Luego ingresamos a el pod mongo-0 para habilitar el cluster de mongoDB

`` kubectl exec -it mongod-0 -- bash``
habilitamos el cluster con el siguiente comando.
``mongosh --quiet``

``` rs.initiate({ _id: "MainRepSet", version: 1,
... members: [
...  { _id: 0, host: "mongod-0.mongodb-service.default.svc.cluster.local:27017" },
...  { _id: 1, host: "mongod-1.mongodb-service.default.svc.cluster.local:27017" },
...  { _id: 2, host: "mongod-2.mongodb-service.default.svc.cluster.local:27017" } ]});
{ ok: 1 } ```

Una vez realizada la operación de crear una base de datos y un objeto en mongo express verificamos ingresando a un pod en este caso en la instancia mongo-1, para ver el cambio que se realizó, se puede apreciar los resultados en las imagenes de captura.

- $ kubectl exec -it mongo-1 sh
 db.getMongo().setReadPref("secondary")
show dbs
use basededatos
show tables
db.basededatos.find()
[
  {
    _id: ObjectId("61a35da5860b43d1d1455543"),
    name: 'Mireia',
    age: 26
  },
  { _id: ObjectId("61a35db6860b43d1d1455544"), name: 'Sergi', age: 21 }
]

## Diferencias que existiría si el montaje se hubiera realizado con el objeto de ReplicaSet

La diferencia que existiría si el montaje se hubiese realizado con el objeto ReplicaSet: es que si muere la instancia y el servicio vuelve a crear una nueva lo identificaria con un identificador diferente, de tal forma que perderiamos el estado de la replica anterior.
En cambio con el objeto StatefulSet, se vuelve a crear un nuevo pod con el mismo identificador que tenia asignado anteriormente.





