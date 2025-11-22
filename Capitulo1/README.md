# 1. Consumir y analizar una API pública

En este laboratorio se espera que el alumno pueda probar una API pública y entender su funcionamiento. 


## Objetivos
- Consumir una API real.
- Analizar sus respuestas HTTP.
- Entender métodos, códigos de estado, headers y cuerpos de respuesta.
- Identificar buenas prácticas básicas.

---
<!--Este fragmento es la barra de 
navegación-->

<div style="width: 400px;">
        <table width="50%">
            <tr>
                <td style="text-align: center;">
                    <a href=""><img src="../images/anterior.png" width="40px"></a>
                    <br>anterior
                </td>
                <td style="text-align: center;">
                   <a href="../README.md">Lista Laboratorios</a>
                </td>
<td style="text-align: center;">
                    <a href="../Capitulo2/"><img src="../images/siguiente.png" width="40px"></a>
                    <br>siguiente
                </td>
            </tr>
        </table>
</div>

---

## Diagrama 

Se espera que el alumno aprenda las bases del consumo de APIs 

![diagrama](../images/1/diagrama.png)



## Instrucciones 
1. Entra a la siguiente API pública.

```bash
https://jsonplaceholder.typicode.com/users
```

2. Desde tu navegador explora el recurso **/users**

3. Responde a las siguientes preguntas:

    - ¿Qué método HTTP utilizó el navegador?
    - ¿Qué código de estado regresó el servidor?
    - ¿Que formato tiene la respuesta? (JSON, XML, etc.)

4. Guarda las respuestas en un archivo de texto. (Comentarlas en clase)

5. Abrir una herramienta profesional **(POSTMAN)**

![alt text](../images/1/1.png)

6. Crear una colección en la herramienta de POSTMAN

![alt text](../images/1/2.png)


7. Realiza las siguientes peticiones:
    - **GET**: */posts*
    - **GET**: */posts/1*
    - **GET**: */comments?postId=1*

![alt text](../images/1/3.png)

8. Registra en un documento de texto lo siguiente: 
    - Código de estado (200, 404, etc.)
    - Headers importantes (Content-Type, Server, Date)
    - Tiempo de respuesta.
    - Tipo de datos devueltos.

9. **Prueba un error**: Envía un GET a una ruta inexistente:

```bash
GET https://jsonplaceholder.typicode.com/xyz123
```


10. Observa lo siguiente: 
    - Código de estado
    - Mensaje de error
    - Cómo responde la API ante recursos inexistentes.

![alt text](../images/1/4.png)

11. **Analiza la estructura de un recurso**: Con el endpoint */users*, analiza: 
    - ¿Qué campos incluye cada usuario?
    - ¿Tiene datos anidados? (por ejemplo: address.geo.lat)
    - ¿Qué tipo de datos es cada campo?

    ![alt text](../images/1/5.png)

12. **Explica qué aprendiste**:

    - ¿Qué es un recurso en una API REST?
    - ¿Cómo se diferencian rutas, parámetros y query strings?
    - ¿Qué te indicó el código de estado?
    - ¿Por qué es importante usar herramientas como Postman?







# Resultado esperado

Al final tanto dentro del navegador web de su elección cómo en la herramienta **POSTMAN** se debería observar una salida similar a lo siguiente. 

![alt text](../images/1/6.png)
