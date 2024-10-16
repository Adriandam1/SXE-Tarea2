# Tarea 2

**A continuación realizo las operaciones de la tarea:**

---

## 1. Descargar la imagen "alpine" SIN ARRANCARLA y comprobar que está en tu equipo
```bash
docker pull alpine
docker images
```
![tarea2-1](https://github.com/user-attachments/assets/5d8b86f9-bca5-4b96-9be7-39ed3ff6c308)

## 2. Crear un contenedor sin ponerle nombre. ¿Está arrancado? Obtén el nombre
```bash
docker create alpine
```
Comprobomanos que no esta arrancado:
```bash
docker ps -a
```
![tarea2-2](https://github.com/user-attachments/assets/bf508601-c0ce-4bbe-ad57-864f78debb3a)

Con el comando anterior ya podemos ver que el nombre del contenedor es: **focused_northcutt**

## 3. Crear un contenedor con el nombre 'dam_alp1'. ¿Cómo puedes acceder a él?
```bash
docker container create -i -t --name dam_alp1 alpine
```
Para iniciarlo y acceder a él utilizamos(para salir ctrl + d):
```bash
docker container start --attach -i dam_alp1
```
![docker1](https://github.com/user-attachments/assets/06c1cdbe-9423-470a-a4a3-03020565635b)

## 4. Comprobar qué IP tiene y si puedes hacer un ping a google.com
Comprobamos la ip con ipa :
```bash
docker exec -it dam_alp1 /bin/sh
ip a
```
Comprobamos que la direccion ip es 172.17.0.2
![dockeripA](https://github.com/user-attachments/assets/fd9dc135-def6-44a1-8b29-5badff90517f)



Tambien podemos inspeccionarlo para sacar mas informacion:
```bash
docker inspect  dam_alp1
```
![docker inspect](https://github.com/user-attachments/assets/46d50cbc-6995-47a9-bdb2-64253168c2f9)

Para realizar el ping a google usaremos:
```bash
docker start dam_alp1
docker exec -it dam_alp1 /bin/sh
ping google.com
```
![docker ping google](https://github.com/user-attachments/assets/d107b378-b3e8-45dc-a652-e34be40270b7)


## 5. Crear un contenedor con el nombre 'dam_alp2'. ¿Puedes hacer ping entre los contenedores?
Nos iremos a otro terminal con alt + f2, creamos el nuevo contenedor, lo iniciamos y hacemos ping a 172.17.0.2 (la ip del primer contenedor)
```bash
docker container create -i -t --name dam_alp2 alpine
docker start dam_alp2
docker exec -it dam_alp1 ping 172.17.0.2
```
Comprobamos que se hacen ping correctamente:

![pingenteecontenedores](https://github.com/user-attachments/assets/1cf6531b-d88a-4e1d-a92f-5fc9d3f72091)


## 6. Salir del terminal, ¿qué ocurrió con el contenedor?
```bash
exit
docker ps
```
Comprobamos que ambos contenedores siguen corriendo, aun saliendo de la terminal

## 7. ¿Cuánta memoria en el disco duro ocupaste?
```bash
docker system df -v
```
![systemdf](https://github.com/user-attachments/assets/7476fbcb-bd06-427e-a10a-4cd56f1dd023)



## 8. ¿Cuánta RAM ocupan los contenedores? ¿Hay algún comando docker para saber esto?
```bash
docker stats
```
![dockerstats](https://github.com/user-attachments/assets/47b0c593-2189-402a-9980-5854c5322c8f)


