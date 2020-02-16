## Apuntes SQL  ##

### SQL ###

SL (`Structure Query Language`) es un lenguaje declarativo. Este tipo de lenguaje se basa en las matemáticas y en la lógica de un lenguaje imperativo. Un lenguaje declarativo no dice cómo hacer una cosa sino que cosa hacer.

En SQL existen varios sublenguajes pero para estos apuntes nos centraremos en DML (`Data Manipulation Language`) que sirve para llevar a cabo las tareas de consulta o manipulación de los datos, organizados por el modelo de datos adecuado.
Dentro de cada sublenguaje existen sentencias que nos servirán para dar una orden específica. En estos apuntes veremos las siguientes sentencias:


- **SELECT** es la palabra clave, significa lo que tenemos que seleccionar en una consulta. 
- **FROM** sirve para decir desde donde se obtienen los datos (`tablas`).
- **WHERE** especifica una condición que debe cumplirse para que los datos sean devueltos por la consulta. Si queremos añadir varias condiciones usaremos *AND* y si queremos escoger una condición o otra usaremos *OR*
- **GROUP BY** especifica la agrupación que se da a los datos.
- **HAVING** especifica una condición que debe cumplirse para que los datos sean devueltos por la consulta. Es muy similar a WHERE pero se diferencia en que el HAVING se aplica al conjunto de resultados devueltos por la consulta. Debe ir acompañado siempre con GROUP BY. 
- **ORDER BY** presenta el resultado ordenado por la columnas indicadas. El orden puede ser ascendente *ASC* y descendente *DESC*. El valor que sale como predeterminado es ascendente.
- **DISTINCT** indica que queremos seleccionar sólo los valores que sean distintos.


### CONSULTAS BÁSICAS ###
Con las sentencias de *SELECT*, *FROM* y *WHERE*. Para  estas consultas básicas usaremos la siguiente tabla ![](https://i.gyazo.com/9a31bc4bc2042be9d891de255913da98.png) 

Una consulta básica sería por ejemplo pedir que nos muestre la población de algún país, en este caso Alemania (`Germany`).

![](https://i.gyazo.com/46a36b58c771f8178526f53f1cfd3c91.png)

El resultado es: 

![](https://i.gyazo.com/dfd7ea5d1f0d2154bf858ab240dc526b.png)

En esta consulta usamos el predicado name = 'Germany'; para ver todos los datos, que se piden, de un nombre que sea igual a Alemania. Si quisiésemos buscar varios nombres a la vez usaríamos name IN ('%','%').

Otra consulta básica sería mostrar el nombre de los países y sus áreas que estén entre 250000 y 300000

![](https://i.gyazo.com/d6ae364303f31a7b8894cfafab8214ef.png)

El resultado es:

![](https://i.gyazo.com/ba9b8927787bff9d7a573be36fecf2c9.png)

En esta consulta usamos el predicado area BETWEEN 250000 AND 300000, en esta consulta para sacar los datos también se podría resolver  con otros predicados como por ejemplo area>= 250000 AND area<=300000 pero sería mucha más largo y rebuscado.

Una consulta que también sería fácil de resolver sería buscar los países que contengan la letra x en su nombre.

![](https://i.gyazo.com/88b32a3e54dfe1ef87310130f6cf0b07.png)

El resultado es:

![](https://i.gyazo.com/48afae29b65aae3a2ac71f10879d101c.png)

En esta consulta usamos el predica name LIKE '%x%' para que nos de el resultado, primero podemos ver como LIKE nos da algo que sea como el valor que le demos en este caso '%x%', el % nos sirve para decir que sea cualquier valor (incluido ninguno o muchos valores), en el caso que quisiéramos que solo fuese un valor fijo usaríamos el _.

### CONSULTAS WORLD ###
En estas consultas usaremos la misma tabla que en las anteriores consultas. Algunas de estas consultas también son simples como las anteriores por lo tanto solo veremos algunas consultas en las que se añada algo nuevo o tenga algo importante.

La primera consulta nos pedirá que nos muestre el nombre y la población en millones para los países del continente de América del sur.

![](https://i.gyazo.com/36bfb44426acfd6a42f76a5fbd212aab.png)

El resultado es:

![](https://i.gyazo.com/a8a3470f366fc9b8441475c83932517e.png)

En esta consulta podemos ver 2 cosas que no habíamos visto, la primera sería que dividimos la población entre 1000000 para que el resultado salga en millones y la segunda es que usamos el ORDER BY name para que se ordene alfabéticamente.

Otra consulta sería la siguiente. Nos pide que enseñemos el GDP per-capita y el nombre del país cuyo GDP valga por lo menos 1 trillón.

![](https://i.gyazo.com/50cb1125380f9f91064494372da11370.png)

El resultado es:

![](https://i.gyazo.com/e4da1c1081e56fe4744e32fef4dd2082.png)

Podemos ver como usamos Round para redondear el resultado, también podemos ver que para calcular el gdp per-capita dividimos el GDP entre la población total.

Una última consulta interesante en esta tabla sería esta. Nos pide que enseñemos el país (`name`) y la capital donde los dos empiece por la misma letra pero sin que tengan el mismo nombre.

![](https://i.gyazo.com/1586d205d7b9f1955a78764312df278e.png)

El resultado es:

![](https://i.gyazo.com/7045875f68aac560a5ce1540e13198c4.png)

Vemos como tenemos que utilizar el LEFT para aislar la primera letra y usamos <> para decir que no pueden ser iguales

### CONSULTAS NOBEL ###
Para estas consultas usaremos la siguiente tabla:

![](https://i.gyazo.com/ee3899bcb9eacb054f47072148494880.png)

La primera consulta nos pide que digamos los ganadores, el año y la materia de todos los ganadores que empiezan por Sir y que ordenemos primero los más recientes y después por nombre.

![](https://i.gyazo.com/2e24ba547de4c60a5038fa51b7c425e0.png)

El resultado es:

![](https://i.gyazo.com/bf0fbdaf0961944e9a39c912de88190d.png)

Podemos ver que usamos el ORDER BY para ordenar primero por año en orden descendiente por eso usamos el DESC y después por nombre como pasa en el 1945 que primero sale Alexander Fleming y después Howard Florey.

La otra consulta que veremos nos pide que enseñemos los ganadores y la materia del año 1984 pero mostrar física  y química los últimos.

![](https://i.gyazo.com/ba4b4e0d9e12402fe61cf99005ae5d91.png)

El resultado es:

![](https://i.gyazo.com/04aa7d83e9253352ac249df4d5c2c0f0.png)

Podemos ver con el ORDER BY subject ponemos que física y química se muestren de manera ascendente, es decir los últimos.

### SUBCONSULTAS ###
Para estas consultas usaremos la siguiente tabla:

![](https://i.gyazo.com/7d15267489be7c9e9f683da92bc62653.png)

La primera consulta que veremos será una subconsulta básica en la cual nos piden que enumeremos los nombres de cada país que tenga una población mayor que Rusia.

![](https://i.gyazo.com/43844bc9ff2b387a0684d32c91f0495f.png)

El resultado es:

![](https://i.gyazo.com/e1b0b839d218feda7e6526e0ae8040ed.png)

Podemos ver que para hacer una subconsulta lo que hay que hacer es poner entre paréntesis la subconsulta que dependerá de la principal.

También hay casos en los que pueden llegar a existir 2 subconsultas como en este que nos pide que hallemos los países cuya población sea mayor que la de Canada pero menor que la de Polonia 

![](https://i.gyazo.com/f903813dd85341190eb445c141adad21.png)

El resultado es:

![](https://i.gyazo.com/d6e6ad76764eeba6cececb469f96cb6b.png)

Podemos ver que hacemos primero una subconsulta para seleccionar canada y despues otra para seleccionar Polonia.

También puede haber subconsultas dentro del *SELECT* como en este caso en el que nos piden que enseñemos el nombre y la población de cada país de Europa y enseñemos la población como un porcentaje de la población de Alemania.

![](https://i.gyazo.com/92be3e64e57d93e5e9ebff30d2dc9ed7.png)

El resultado es:

![](https://i.gyazo.com/f79e0d1670fb59d491576de02935222b.png)

En esta subconsulta usamos un CONCAT para poder tener el símbolo de porcentaje y el ROUND para redondear a decimal. Vemos que dividimos la población de un país cualquiera entre la una subconsulta que es siempre la población de Alemania.

### SUM Y COUNT ###
Para estas consultas usaremos la siguiente tabla:

![](https://i.gyazo.com/7d15267489be7c9e9f683da92bc62653.png)

Para estas consultas hace falta saber la función que tenien *SUM* y *COUNT*. 

La función de *SUM* sirve para sumar todos los valores como en este caso por ejemplo:

![](https://i.gyazo.com/6e356e16af751cc2cc85401ad5e94105.png) 

El resultado sería este:

![](https://i.gyazo.com/b164eb553d52a0857637659449b1183c.png)

La función de *COUNT* sirve para contar el número de algo. En este caso los paises con una area mayor a 1000000

![](https://i.gyazo.com/f242953ddfb0736c25a2b589e3d932d0.png)

El resultado es:

![](https://i.gyazo.com/9a76ce986f726947bfc715bf99eacce9.png)

Esto se puede combinar con GROUP BY y HAVING. Si nos pidieran una lista de continentes que tengan una población de al menos 100 millones los haríamos así

![](https://i.gyazo.com/7781aee085b1c311b43a3d393f1f24e3.png)

El resultado sería este:

![](https://i.gyazo.com/aba39c44bf1036e10fda87be444fd196.png)

### CONSULTAS CON JOIN ###
Para estas consultas usaremos las siguientes tablas:

![](https://i.gyazo.com/1c4edd4eac74c48af2e5853ebb75939c.png)

![](https://i.gyazo.com/5362565c6d5da500166af2fb527a2759.png)

![](https://i.gyazo.com/0710576faf50740d6e844f01640fe5c8.png)

![](https://i.gyazo.com/3f269b5b49cb6837a5040423d53a56f9.png)

Una consulta simple con *JOIN* sería la siguiente, en la cual nos piden que enseñemos los jugadores, los id de los equipos, el estadio y el día del partido en los cuales marcó un gol Alemania.

![](https://i.gyazo.com/d95b850d4dcf9008f37a4f4600453ba0.png)

El resultado es:

![](https://i.gyazo.com/931108373869b4949e6c8ee8a3d8a456.png)

Como podemos ver usamos *JOIN* debido a que se necesitan más de dos tablas para sacar la información que nos pide el ejercicio, al usar *JOIN* tenemos que igualar dos valores de cada tabla para poder relacionarlas.

En esta consulta nos piden que mostremos el id del partido la fecha y el numero de goles que marco Alemania en todos sus partidos.

![](https://i.gyazo.com/6c3de89550b9b03d9b888be17568c452.png)

El resultado es:

![](https://i.gyazo.com/687adf934733bee4722c6ea2c037524d.png)

### OTRAS CONSULTAS CON JOIN ###
Para estas consultas usaremos las siguientes tablas:

![](https://i.gyazo.com/b76bad675373c10d48bef5d55da425ea.png)

Dentro de este tipo de consultas también pueden existir subconsultas como en este caso que nos piden que hagamos una lista con los titulos de las peliculas y el nombre del actor principal de cada una, en estas películas tiene que actuar Julie Andrews.

![](https://i.gyazo.com/b8889ac7a6c0703a692e4c03cf44ca20.png)

El resultado es:

![](https://i.gyazo.com/8c5f88b88c1a2753f06d078daf5ae238.png)

Otra manera de usar los *JOINS* sería esta. Nos piden que mostremos el casting de la pelicula Alien.

![](https://i.gyazo.com/137004e91c0c9d604bf3e4bb90de9d1f.png)

El resultado es:

![](https://i.gyazo.com/3b75c34412dfe2c24c0f64c606488326.png)

De esta manera podemos coger información de varias tablas sin tener que escribir el *JOIN* pero consiguiendo el mismo resultado.

Tambien podemos combinar *JOIN* con *GROUP BY* y *HAVING*. En esta consulta nos pide que obtengamos una lista, en orden alfabético, de los actores que hayan sido protagonistas al menos 15 veces.

![](https://i.gyazo.com/ef58626ce1ca6d8325f59c9b7b078630.png)

El resultado es:

![](https://i.gyazo.com/2722c5cbad6cb065561a30c788d27795.png)

En esta consulta nos pide que hagamos una lista con todos los nombres de los actores que hayan trabajado con 'Art Garfunkel'. 

![](https://i.gyazo.com/97daa5f3ed88b2f203476424e2ac66d0.png)

El resultado es:

![](https://i.gyazo.com/18f9996f8f302fb8c229ef8b5f3f1050.png)

Utilizamos el *DISTINCT* para que el nombre de los actores no se repita, por si han trabajado en más de una película juntos.
