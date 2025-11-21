# 4. Implementando autenticación con API Key, Tokens y buenas prácticas de seguridad en APIs

Usando APIs públicas probar los métodos de autenticación **API Key** y **Bearer Token**. Analizar los resultados. 

## Objetivos
- Entienda cómo funcionan los mecanismos de autenticación más usados en APIs.
- Use API Keys en cabeceras.
- Use Tokens Bearer simulando JWT.
- Analice respuestas de error y códigos HTTP de seguridad.


---

<div style="width: 400px;">
        <table width="50%">
            <tr>
                <td style="text-align: center;">
                    <a href="../Capitulo3/"><img src="../images/anterior.png" width="40px"></a>
                    <br>anterior
                </td>
                <td style="text-align: center;">
                   <a href="../README.md">Lista Laboratorios</a>
                </td>
<td style="text-align: center;">
                    <a href="../Capitulo5/"><img src="../images/siguiente.png" width="40px"></a>
                    <br>siguiente
                </td>
            </tr>
        </table>
</div>

---

## Diagrama

![diagrama](../images/4/diagrama.png)



## Instrucciones

---
### Autenticación con API Key
Se usará la API de **API Ninjas**, que requiere API Key en la cabecera.

1. Crear una cuenta gratuita en:

```bash
https://api-ninjas.com/
```

2. Usar una cuenta de Google para registrarse. 

![alt text](../images/4/1.png)


3. Obtener una API Key.

![alt text](../images/4/2.png)


4. En Postman crear una nueva colección que llamaremos **lab4**

5. Crear una nueva petición en **Postman** con el siguiente URL.

```bash
https://api.api-ninjas.com/v1/country?name=United States
```

![alt text](../images/4/3.png)

6. En los headers agregar 

```bash
X-Api-Key: <Tu API Key>
```

![alt text](../images/4/4.png)

5. Enviar la petición 

![alt text](../images/4/5.png)

6. Quitar la API Key y volver a enviar. Y debería de observar el siguiente resultado.  

![alt text](../images/4/6.png)

7. Comparar ambas respuestas. 
---


---
### Autenticación tipo Token Bearer (Simulación)
Se usará el endpoint de reqres.in, que valida si el token Bearer existe o no.

1. Crear nueva petición POST, este url simula la obtención del JWT para al autenticación:

```bash
https://reqres.in/api/login
```

2. Para que la simulación funcione bien añadir el header:

![alt text](../images/4/7.png)

3. En el Body enviar el siguiente body:

```json
{
  "email": "eve.holt@reqres.in",
  "password": "cityslicka"
}
```

4. Si se envía el request se debería observar el siguiente resultado:

![alt text](../images/4/8.png)

5. Hacer otra petición con el token obtenido, con el siguiente URL:

```bash
GET https://reqres.in/api/users/2
```

6. Añadir el método de autenticación Bearer:


![alt text](../images/4/9.png)

7. Enviar el **Request**

![alt text](../images/4/10.png)

---


## Resultado Esperado 

Al final el alumno debería de tener los siguientes **request**

![alt text](../images/4/11.png)
