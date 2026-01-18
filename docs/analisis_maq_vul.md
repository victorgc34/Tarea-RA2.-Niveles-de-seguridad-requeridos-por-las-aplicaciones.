# Apartado 2 - Análisis de vulnerabilidad

En este apartado, se analiza la vulnerabilidad **“SQL Injection (GET/SEARCH)”** de el entorno “bWAPP”. Concretamente, se centra en el análisis del código que permite esta vulnerabilidad se explotada por los atacantes. El despliegue de este entorno se realiza en una máquina virtual de Kali linux dentro de Docker.

---

### **Identificación del endpoint vulnerable**

En la siguiente captura, podemos observar que hay un campo al cual podemos buscar diferentes nombres de películas. 

![](img-2/inicio.png)

Para comprobar la vulnerabilidad, introduciremos un carácter usado en las consultas de SQL para ver si nos da algún error.

![](img-2/inicio-vul.png)

Concretamente nos da un error de sintaxis de SQL, por lo que significa que el carácter puesto esta realizando una función dentro de backend (concretamente cerrando una parte de la consulta cuando no debería).

---

## Explotación de la vulnerabilidad

Con la información anterior, podemos inyectar código sql a través del mismo input del html. Además, para que resulte algo más sencillo las pruebas, en la misma url podríamos meter todo nuestro código malicioso. 

En este caso, muestro una simple inyección de sql que me permite obtener todo el listado de películas que se encuentran en la tabla.

---

## Análisis del código vulnerable

Para ello, lo primero que haremos será revisar el código php que la crea la página anterior que nosotros podemos observar en html.

El código mostrado es el que se encuentra en la ruta: **/var/www/html/sqli_1.php**

![](img-2/input-tittle.png)

En la imagen anterior, podemos ver que el propio html identifica el texto que nosotros añadimos por el input como “tittle”.

![](img-2/php-tittle.png)

Concretamente, podemos ver como se procesa esa variable que lleva nuestro código, por lo que podemos identificar que **la única validación que realiza sobre nuestra entrada es de “si existe”.** Por lo que el propio código nos permite inyecta código a la consulta de la base de datos.

```python
$sql = "SELECT * FROM movies WHERE title LIKE '%" . sqli($title) . "%'";
```

Toda esta información la podemos usar para realizar consultas a la base de datos mas perniciosas, que pueden llegar a vulnerar la máquina y comprometer la seguridad de la misma.
