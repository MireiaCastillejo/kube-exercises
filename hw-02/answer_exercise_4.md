EXERCISE 4
==========
# 4. Crear un objeto de tipo deployment con las especificaciones del ejercicio 1.
• Despliega una nueva versión de tu nuevo servicio mediante la técnica “recreate”
• Despliega una nueva versión haciendo “rollout deployment”
• Realiza un rollback a la versión generada previamente

Deployment recreate:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  strategy: 
    type: Recreate
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.19.4
          resources:
            requests:
              memory: "156Mi"
              cpu: "100m"
            limits:
              memory: "256Mi"
              cpu: "100m"
```
Creamos el deployment:
`kubectl apply -f deployment-recreate.yaml`

Deployment rollout deployment:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  strategy: 
    type: RollingUpdate
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.19.4
          resources:
            requests:
              memory: "156Mi"
              cpu: "100m"
            limits:
              memory: "256Mi"
              cpu: "100m"

````
Creamos el deployment:
`kubectl apply -f deployment-rollout.yaml`

Obtenemos el historial de versiones
`kubectl rollout history deployment nginx-deployment`

Realizamos el rollout a la versión generada previamente:
`kubectl rollout undo deployment nginx-deployment --to-revision=1`