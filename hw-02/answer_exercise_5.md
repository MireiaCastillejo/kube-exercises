# Ejercicio 5

## 5. Diseña una estrategia de despliegue que se base en ”Blue Green”. Podéis utilizar la imagen del ejercicio 1.
1. Creamos un objeto deployment de la versión 1
`kubectl apply -f deployment-blue.yaml`
2. Se crea un servicio que apunte al deployment creado
`kubectl apply -f service-blue.yaml`
3. Creamos un objeto deployment de la version 2
`kubectl apply -f deployment-green.yaml`
4. Se crea un servicio que apunte al deployment (version 2)
`kubectl apply -f service-green.yaml`
5. Se realiza un switch del tráfico a la versión 2, haciendo que el servicio que apuntaba a la primera versión pase apuntando a la segunda.
`kubectl patch service blue-service -p '{"spec":{"selector":{"version": "1.19.6"}}}'`