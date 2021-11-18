# Ejercicio 3

## Crea un objeto de tipo service para exponer la aplicación del ejercicio anterior de las siguientes formas:
• Exponiendo el servicio hacia el exterior (crea service1.yaml)
• De forma interna, sin acceso desde el exterior (crea service2.yaml)
• Abriendo un puerto especifico de la VM (crea service3.yaml)

Servicio al exterior:
`kubectl apply -f service1.yaml`
`kubectl get svc`
`kubectl describe service nginx-service1`


