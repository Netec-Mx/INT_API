# 5. API Gateway Kong para administrar acceso a APIs
Se necesita crear una alerta que le avise al equipo cuando un microservicio se ha caido. 

## Objetivos
- Configurar Kong en modo DB-less usando un archivo declarativo (kong.yaml).
- Exponer los apis client y item bajo un único API Gateway.
- Validar el comportamiento del Gateway desde el punto de vista del consumidor de APIs.

---
<div style="width: 400px;">
        <table width="50%">
            <tr>
                <td style="text-align: center;">
                    <a href="../Capitulo4/"><img src="../images/anterior.png" width="40px"></a>
                    <br>anterior
                </td>
                <td style="text-align: center;">
                   <a href="../README.md">Lista Laboratorios</a>
                </td>
<td style="text-align: center;">
                    <a href="."><img src="../images/siguiente.png" width="40px"></a>
                    <br>siguiente
                </td>
            </tr>
        </table>
</div>

---


## Diagrama

![diagrama](../images/5/diagrama.png)


> **NOTA:** Asegurarse que este iniciado el motor de Docker para que se puedan iniciar los contenedores que usaremos en la práctica.

## Instrucciones

1. En el escritorio crear una carpeta que llamaremos lab5

2. Dentro de la carpeta añadiremos 2 archivos:
    - **docker-compose.yaml**
    - **kong.yaml**

3. Dentro del archivo **docker-compose.yaml** añadiremos el siguiente contenido: 

```yaml
services:
  mysqlserver:
    container_name: mysqlserver
    image: "mysql:8.0"
    environment:
      - MYSQL_ROOT_PASSWORD=netec123
      - MYSQL_DATABASE=items
    healthcheck:
      test: mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} -hlocalhost
  
  microitem:
    container_name: microitem
    image: edgardovefe/apis:microitem
    environment:
      - IP_DB=mysqlserver
      - PORT_DB=3306
      - NAME_DB=items
      - USER_DB=root
      - PASSWORD_DB=netec123
    ports:
      - 8083:8083
    depends_on:
      mysqlserver:
        condition: service_healthy
    healthcheck:
      test: curl -f http://localhost:8083/item
  
  microclient:
    container_name: microclient
    image: edgardovefe/apis:microclient
    ports:
      - 8084:8084
    healthcheck:
      test: curl -f http://localhost:8084/client
  

  kong:
    container_name: kong
    image: kong:3.5
    environment:
      KONG_DATABASE: "off"
      KONG_ADMIN_LISTEN: 0.0.0.0:8001
      KONG_DECLARATIVE_CONFIG: /kong/kong.yaml
    ports:
      - "8000:8000" # Gateway público
      - "8001:8001" # Admin
    volumes:
      - ./kong.yaml:/kong/kong.yaml:ro
    depends_on:
      - microclient
      - microitem
```

4. Dentro del archivo **kong.yaml** añadiremos el siguiente contenido: 

```yaml
_format_version: "3.0"
_transform: true

services:
  - name: clientes-service
    url: http://microclient:8084
    routes:
      - name: clientes-route
        paths:
          - /api1

  - name: items-service
    url: http://microitem:8083
    routes:
      - name: items-route
        paths:
          - /api2
```

5. Dentro del archivo de **kong.yaml** podemos ubicar lo siguiente:

- Se definen las rutas para conectarse a nuestros apis

- Se define el sufijo de cada ruta **/api1** para client y **/api2** para item. 

5. Se abre una terminal dentro de la carpeta **lab5**

![alt text](../images/5/1.png)

6. Ejecutar el siguiente comando:

```bash
docker-compose up -d
```

> **NOTA:** Esperar que el comando termine de ejecutarse, tardará unos minutos ya que tiene que descargar las imagenes de cada uno de los contenedores

7. Al terminar de ejecutarse el comando deberíamos de observar lo siguiente en la terminal:


![alt text](../images/5/2.png)


8. Válida con el siguiente comando que los contenedores esten iniciados:

```bash
docker ps
```

![alt text](../images/5/3.png)



9. Abrir postman y probar el siguiente url con el método **GET**, para conectarse al api clients:


```bash
http://localhost:8000/api1/client
```

![alt text](../images/5/4.png)

10. Abrir otro request en **Postman** y probar el siguiente url para conectarse al API items

```bash
http://localhost:8000/api2/item
```

![alt text](../images/5/5.png)

11. Podemos observar que ambos request se conectan al mismo puerto **8000** porque nos conectamos por el API gateway **kong**

12. Fin práctica


## Resultado Esperado [Instrucciones](#instrucciones)

Al final del laboratorio los alumnos tendrán 2 requests que se conectan al **API Gateway Kong**

![alt text](../images/5/6.png)
