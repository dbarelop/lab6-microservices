## 1. Registering `accounts` and `web` microservices
![accounts and web microservices registered](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.06.34.png)
After starting `accounts` and `web` microservices in ports 2222 and 3333, respectively, Eureka's console at http://localhost:1111 will display the show both services are UP:
![Eureka's console after registering accounts and web microservices](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.06.55.png)
## 2. Registering an additional `accounts` microservice
![Two accounts and one web microservices registered](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.07.10.png)
Eureka's console shows there's a second `accounts` service running in port 4444:
![Eureka's console after registering another accounts service](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.07.21.png)
## 3. Making a request to the `accounts` service
If we request some information to the `accounts` service, we can see that only the one running at port 2222 gets the request:
![Requests to the accounts service are served by the one running at port 2222](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.07.38.png)
## 4. Killing the first `accounts` service
![The first accounts service is killed](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.07.51.png)
Eureka's console displays now only the `accounts` microservice running at :4444.
![Eureka's console after killing the first accounts service](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.08.01.png)
## 5. Making another request to the `accounts` service
If we make a request to the `accounts` service immediately after killing the one that was previously serving our requests we will get an error, because the `web` service will still have the previous address of `accounts` and it won't be able to connect.
After a few seconds, the `register` service will tell the `web` service the new address for the `accounts` service, and the same request will be redirected to the second `accounts` service, successfully returning the requested information:
![The web service fails to connect with the accounts service at the initial address and successfully connects after receiving the new address from the register server](https://github.com/dbarelop/lab6-microservices/blob/test/screenshots/Captura de pantalla 2017-01-13 a las 13.08.24.png)
