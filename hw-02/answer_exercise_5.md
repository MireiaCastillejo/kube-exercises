# Ejercicio 5

## 5. Diseña una estrategia de despliegue que se base en ”Blue Green”. Podéis utilizar la imagen del ejercicio 1.
1. Creamos un objeto deployment de la versión 1
`kubectl apply -f deployment-blue.yaml`
2. Se crea un servicio que apunte al deployment creado
`kubectl apply -f service.yaml`
3. Creamos un objeto deployment de la version 2
`kubectl apply -f deployment-green.yaml`
4. Validamos que el servicio apunta al deployment-blue
`kubectl describe service blue-green` 
          <img width="598" alt="Captura de pantalla 2021-11-20 a las 10 35 27" src="https://user-images.githubusercontent.com/26769446/142721721-bf22ff64-1da2-4498-acfd-d76c7b5fea77.png">
5. Se realiza un switch del tráfico a la versión 2, haciendo que el servicio que apuntaba a la primera versión pase apuntando a la segunda.
`kubectl patch service blue-green -p '{"spec":{"selector":{"version": "2.0"}}}'`

6. Una vez realizado el cambio, volvemos a validar que el servicio apunta al deployment-green
`kubectl describe service blue-green`
      <img width="1435" alt="Captura de pantalla 2021-11-20 a las 10 36 42" src="https://user-images.githubusercontent.com/26769446/142721713-ac152bdf-fabe-441e-96f3-adb0aa826b16.png">
