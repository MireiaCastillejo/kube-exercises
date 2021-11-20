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

<img width="764" alt="Captura de pantalla 2021-11-20 a las 12 02 50" src="https://user-images.githubusercontent.com/26769446/142723917-11a44a09-35da-42bd-bf07-e6a221d086ee.png">

3. Vemos la información de cada servicio
```
kubectl describe service nginx-service1
```
<img width="751" alt="Captura de pantalla 2021-11-20 a las 12 02 21" src="https://user-images.githubusercontent.com/26769446/142723924-cc19d83f-cdf1-4c88-9bfe-fb5acabb927e.png">

```
kubectl describe service nginx-service2
```
<img width="751" alt="Captura de pantalla 2021-11-20 a las 11 14 39" src="https://user-images.githubusercontent.com/26769446/142722709-489f706a-ee4b-4b5b-bb99-65cdc8acec56.png">

``` 
kubectl describe service nginx-service3 
```

<img width="751" alt="Captura de pantalla 2021-11-20 a las 11 14 52" src="https://user-images.githubusercontent.com/26769446/142722720-29e9a542-19d4-4dd9-8798-e88dcd6901be.png">
