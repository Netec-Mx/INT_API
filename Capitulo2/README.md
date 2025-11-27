# Práctica 2. Explorando una petición HTTP completa usando Postman y cURL
En este laboratorio identificarás y analizarás los componentes de una petición HTTP (método, URL, headers, body), además, comprenderás la estructura de una respuesta HTTP (código de estado, headers y cuerpo de respuesta).


## Objetivos
- Identificar los componentes de un HTTP request.
- Comprender la estructura de una respuesta HTTP.
- Analizar códigos de estado, headers y cuerpo de respuesta.

---
<div style="width: 400px;">
        <table width="50%">
            <tr>
                <td style="text-align: center;">
                    <a href="../Capitulo1/"><img src="../images/anterior.png" width="40px"></a>
                    <br>anterior
                </td>
                <td style="text-align: center;">
                   <a href="../README.md">Lista Laboratorios</a>
                </td>
<td style="text-align: center;">
                    <a href="../Capitulo3/">
                    <img src="../images/siguiente.png"
                     width="40px"></a>
                    <br>siguiente
                </td>
            </tr>
        </table>
</div>

---

![Implementacion](../images/2/diagrama.png)

<br>

## Instrucciones

### Tarea 1. Enviar una petición GET.

**Paso 1.** Abrir **Postman**.

**Paso 2.** Crear una nueva colección llamada **lab2**.

**Paso 3.** Seleccionar el método **GET**.

**Paso 4.** En el campo **URL**, escribir:

```bash
https://jsonplaceholder.typicode.com/posts/1
```

**Paso 5.** <ins>No</ins> enviar headers ni body adicionales.

**Paso 6.** Dar click en **enviar**.

![alt text](../images/2/1.png)


### Tarea 2. Analiza la respuesta de la petición GET.

Despúes de enviar la petición, debes de identificar:

**Paso 1.** El código de estado:

  - Verifica si el API regresó un 200 OK.

![alt text](../images/2/2.png)

**Paso 2.** Headers de respuesta. Localiza lo siguiente:

  - Content-Type.
  - Connection.
  - Date.
  - Server.

![alt text](../images/2/3.png)

**Paso 3.** Cuerpo (body) de la respuesta. Identifica lo siguiente:

  - userId.
  - id.
  - title.
  - body.

![alt text](../images/2/4.png)

---

### Tarea 3. Enviar una petición POST con body JSON.

**Paso 1.** Dentro de la misma colección, crea una nueva petición.

**Paso 2.** Selecciona el método **POST**.

**Paso 3.** Escribe la siguiente URL:

```bash
https://jsonplaceholder.typicode.com/posts
```

**Paso 4.** Ir a la pestaña de **`body`** -> **`raw`** -> **`JSON`**.

**Paso 5.** Escribir el siguiente **JSON**:

```json
{
  "title": "Curso APIs",
  "body": "Prueba de creación de recurso",
  "userId": 123
}
```

**Paso 6.** Enviar la petición.

![alt text](../images/2/5.png)

### Tarea 4. Analizar el resultado del POST.

Identificar lo siguiente:

**Paso 1.** Headers enviados por el servidor.

  - **Content-Type**: application/json.
  - **Content-Length**.

![alt text](../images/2/6.png)

**Paso 2.** Código de estado esperado.

  - 201 Created.

![alt text](../images/2/7.png)

**Paso 3.** <ins>Body esperado</ins>: el API debe de regresar el objetivo enviado, agregando un campo **id**.

![alt text](../images/2/8.png)

---

## Resultado esperado

  - Al final, deberás de tener los <ins>2 request</ins> de HTTP en **Postman**.

![alt text](../images/2/9.png)
