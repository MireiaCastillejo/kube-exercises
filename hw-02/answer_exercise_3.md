# Ejercicio 3

## Crea un objeto de tipo service para exponer la aplicación del ejercicio anterior de las siguientes formas:
- Exponiendo el servicio hacia el exterior (crea service1.yaml)
- De forma interna, sin acceso desde el exterior (crea service2.yaml)
- Abriendo un puerto especifico de la VM (crea service3.yaml)

1. Aplicamos cada servicio con el comando :
```
  kubectl apply -f service1.yaml
  kubectl apply -f service2.yaml
  kubectl apply -f service3.yaml
```
2. Vemos los servicios:
```
  kubectl get svc
  ```
 <img width="960" alt="Captura de pantalla 2021-11-18 a las 21 28 35" src="https://user-images.githubusercontent.com/26769446/142722054-1cd3b73b-e1c3-4d8d-89b7-45d7bd502fc8.png">

3. Vemos la información de cada servicio
```
kubectl describe service nginx-service1
```
<img width="751" alt="Captura de pantalla 2021-11-20 a las 11 14 13" src="https://user-images.githubusercontent.com/26769446/142722691-60af0c8d-5ddd-4142-b75e-1500cfad7005.png">
```
kubectl describe service nginx-service2
```
<img width="751" alt="Captura de pantalla 2021-11-20 a las 11 14 39" src="https://user-images.githubusercontent.com/26769446/142722709-489f706a-ee4b-4b5b-bb99-65cdc8acec56.png">
```
kubectl describe service nginx-service3
```
<img width="751" alt="Captura de pantalla 2021-11-20 a las 11 14 52" src="https://user-images.githubusercontent.com/26769446/142722720-29e9a542-19d4-4dd9-8798-e88dcd6901be.png">
