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
docker create --name=dam_alp1 alpine
$docker start -ai dam_alp1
```
![tarea2-3](https://github.com/user-attachments/assets/6db0f593-1ba2-4e8b-a1ff-f2cacd2527d3)


### DE AQUI EN ADELANTE PENDIENTE DE COMPLETAR!!!
### ------------------------------------------------------------------
### ------------------------------------------------------------------


## 4. Comprobar qué IP tiene y si puedes hacer un ping a google.com
```bash
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' dam_alp1
docker exec -it dam_alp1 ping google.com
```
## 5. Crear un contenedor con el nombre 'dam_alp2'. ¿Puedes hacer ping entre los contenedores?
```bash
docker create --name=dam_alp2 alpine
docker exec -it dam_alp1 ping <IP_de_dam_alp2>
```
## 6. Salir del terminal, ¿qué ocurrió con el contenedor?
```bash
exit
docker ps
```
## 7. ¿Cuánta memoria en el disco duro ocupaste?
```bash
docker system df
```
![tarea2-7](https://github.com/user-attachments/assets/fd0bd1a1-1209-4abe-8e1b-57108ba396e4)


## 8. ¿Cuánta RAM ocupan los contenedores? ¿Hay algún comando docker para saber esto?
```bash
docker stats
```
