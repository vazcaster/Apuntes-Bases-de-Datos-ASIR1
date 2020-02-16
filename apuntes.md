## Apuntes SQL  ##

### SQL ###

SQL (`Structure Query Language`) es un lenguaje declarativo. Este tipo de lenguaje se basa en las matemáticas y en la lógica de un lenguaje imperativo. Un lenguaje declarativo no dice cómo hacer una cosa sino que cosa hacer.

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

### CONSULTAS WORLD 

En estas consultas usaremos la misma tabla que en las anteriores consultas. Algunas de estas consultas también son simples como las anteriores por lo tanto solo veremos algunas consultas en las que se añada algo nuevo o tenga algo importante.

La primera consulta nos pedirá que nos muestre el nombre y la población en millones para los países del continente de América del sur.

![](https://i.gyazo.com/36bfb44426acfd6a42f76a5fbd212aab.png)

El resultado es:

![](https://i.gyazo.com/a8a3470f366fc9b8441475c83932517e.png)

En esta consulta podemos ver 2 cosas que no habíamos visto, la primera sería que dividimos la población entre 1000000 para que el resultado salga en millones y la segunda es que usamos el ORDER BY name para que se ordene alfabéticamente.