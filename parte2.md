## CLASE DE GROUP BY:

*- En este ejemplo usaremos COUNT, esto nos sirve para contar todos los registros de la tabla que queremos, te lo mostrare en el siguiente ejemplo:

```
  SELECT COUNT (*) 
  FROM personas
```

*- En este ejemplo usaremos COUNT con GROUP BY para agrupar un conteo de una columna en especifica como lo es sexo, te lo mostrare en el siguiente ejemplo:

```
  SELECT sexo, COUNT (*) 
  FROM personas 
  GROUP BY sexo
```

*- En este ejemplo usaremos MAX y dentro de los () la columna precio para obtener el precio mayor de los libros AS se usa para darle un alias a la columna de precios ya que al poner MAX pondra eso en la columna y al poner El AS podemos ponerle un alias justo como esta en el ejemplo, te lo mostrare en el siguiente ejemplo:

```
  SELECT nombreeditorial, MAX (precio) AS preciomayor 
  FROM libros 
  GROUP BY nombreeditorial;
```

*- En este ejemplo usaremos MIN para obtener el minimo precio de los libros, el mismo ejemplo de arriba pero con MIN en vez MAX, te lo mostare en el siguiente ejemplo:

```
  SELECT nombreeditorial, MIN (precio) AS preciomenor 
  FROM libros 
  GROUP BY nombreeditorial;
```

*- En este ejemplo usaremos MIN y MAX para obtener el precio mayor y el menor en una sola consulta, te lo mostrare en el siguiente ejemplo:

```
  SELECT nombreeditorial, MIN(precio) AS preciomenor, MAX(precio) AS preciomayor 
  FROM libros 
  GROUP BY nombreeditorial;
```

*- En este ejemplo usaremos COUNT para hacer un conteo donde WHERE nos muestre los precios y BETWEEN sirve para darnos un rango de precios entre 100 y 300 usando el operador AND 

```
  SELECT nombreeditorial, COUNT(*) 
  FROM libros 
  WHERE precio BETWEEN 100 AND 300 
  GROUP BY nombreeditorial 
```

## CLASE DE HAVING:

*- En este ejemplo usaremos HAVING porque where Se utiliza para filtrar filas antes de que se realice cualquier operación de agrupación,se aplica a las filas individuales de la tabla, HAVING: Se utiliza para filtrar los resultados después de que se han realizado las operaciones de agrupación, HAVING se aplica a los grupos de filas creados por GROUP BY

```
  SELECT email, COUNT(*) 
	FROM users  
	GROUP BY email 
	HAVING COUNT(*) > 1
	ORDER BY COUNT(*) DESC;
```

## CLASE DE LLAVE PRIMARA (PRIMARY KEY): 

*- En este ejemplo te explicare para que sirve la llave primaria o PRIMARY KEY, esta sirve para identificar la columna donde la coloquemos como unica, para no tener datos repetidos, su abreviatura es PK. te lo mostrare en el siguiente ejemplo:

```
  CREATE TABLE libros(
	codigolibro INTEGER PRIMARY KEY,
	titulo VARCHAR(40),
	autor VARCHAR(30),
	nombreeditorial VARCHAR(45),
	precio DECIMAL(5,2),
	cantidad SMALLINT
	);
```

## CLASE DE JOINS: 

*- En este ejemplo vamos explicar como unir dos o mas tablas para eso usaremos los JOIN, los JOIN sirven para poder combinar filas de dos o mas tablas basandonos en una CLAVE FORANEA (FOREIGN KEY).

*- En este ejemplo te explicare Que es una  CLAVE FORANEA (FOREIGN KEY), esta nos va a servir para que nosotros podamos relacionar dos tablas.

*- En este ejemplo te mostraremos como usar INNER JOIN que lo usaremos para unir las tablas de clientes y pedidos, ponemos los datos de ambas tablas en SELECT y luego le decimos de que tabla con un FROM y luego le decimos con INNER JOIN pedidos que las una, luego ponemos para activarlas un ON pero le damos alias a la tabla cliente y pedidos, tambien le ponemos el alias que le pusimos a las tablas se lo pones a los datos, te lo mostrare en el siguiente ejemplo:

```
  SELECT p.idpedido, p.descripcion, p.fecha, c.idcliente, c.nombre, 
  c.apellidopaterno, c.apellidomaterno
	FROM clientes c
	INNER JOIN pedidos p
	ON c.idcliente = p.idcliente;
```

*- Haremos otro ejemplo de como usar INNER JOIN diferente al de arriba, recordar que las letras e y i son alias que le daremos a las tablas para usarlas en ON que ON seria EN (en español), te lo mostrare en el siguiente ejemplo:

```
  SELECT * FROM estudiantes e
	INNER JOIN infoestudiantes i
	ON e.idestudiante = i.id_estudiante;
```

## CLASE DE LEFT JOIN: 

*- El LEFT JOIN nos sirve para poder investigar que registro de una tabla no se encuentra en la otra tabla, en este ejemplo pusimos la tablas al reves la que iba de segunda la ponemos de consulta para poder hacer la busqueda en la tabla libros, te lo mostrare en el siguiente ejemplo:

```
  SELECT * FROM editorial 
	LEFT JOIN libros 
	ON editorial.codigo_editorial = libros.codigolibro
	ORDER BY codigolibro ASC 
```

*- El LEFT JOIN  a diferencia del INNER JOIN donde se busca una union de las dos tablas o sea se muestran los valores donde unicamente coicidan los registros 
de las columnas de ambas tablas, con LEFT JOIN le vamos a dar prioridad a la tabla izquierda  en este caso en la tabla puesto y vamos a buscar en la tabla derecha, vamos a buscar en la tabla empleados si hay empleados con ese puesto, si no hay concidencias en las tablas entonces las columnas aparecen en null
te lo mostrare en el siguiente ejemplo: 

```
  SELECT * FROM puestos p
	LEFT JOIN empleados e 
	ON p.puestoid = e.puestoid
	ORDER BY p.puestoid ASC
```

*- En este ejemplo haremos un LEFT JOIN con un GROPU BY ya sabemos que si usamos COUNT (*) debemos poner GROUP BY  no ORDER BY, bueno aqui usaremos EL LEFT JOIN  mas el GROUP BY para obtener un conteo de la cantida de nombre editorial, RECORDAR QUE EL CONTEO SE HACE POR CUANTAS VECES SE REPITA EL codigo_editorial, si hay cinco de 224 entonces aparecera que hay cantidad de 5

```
  SELECT e.nombreeditorial, COUNT (*)
	FROM editorial e
	LEFT JOIN libros l 
	ON e.codigo_editorial = l.codigoeditorial
	GROUP BY e.nombreeditorial
```

*- En este ejemplo usaremos el mismo LEFT JOIN mas un GROUP BY pero a diferencia que en SELECT, hacemos dos consultas y le ponemos un alias al COUNT con el AS y le ponemos de alias cantidad, recordar poner lo que colocas en consulta ponerlo de nuevo en GROUP BY para que no tire error en el Query

```
  SELECT e.nombreeditorial,e.codigo_editorial, COUNT (*) AS Cantidad
	FROM editorial e
	LEFT JOIN libros l 
	ON e.codigo_editorial = l.codigoeditorial
	GROUP BY e.nombreeditorial,e.codigo_editorial
```

*- En este ejemplo usaremos LEFT JOIN, COUNT, GROUP BY, ORDER BY, aqui usaremos todos estos unidos y en COUNT en vez COUNT (*) le ponemos dentro COUNT (l.codigoeditorial) le ponemos esa columna para mostrar el resgistro de los libros  

```
  SELECT e.nombreeditorial, e.codigo_editorial, COUNT (l.codigoeditorial) AS Cantidad
	FROM editorial e
	LEFT JOIN libros l 
	ON e.codigo_editorial = l.codigoeditorial
	GROUP BY e.nombreeditorial,e.codigo_editorial 
	ORDER BY e.codigo_editorial ASC
```

## CLASE DE RIGHT JOIN: 

*- El RIGHT JOIN se le da prioridad a la tabla derecha, te lo mostrare en el siguiente ejemplo: 

```
	SELECT * FROM empleados e              < nota para mi: siempre tabla izquierda  
	RIGHT JOIN puestos p                   < nota para mi: siempre es la tabla derecha asi sea INNER JOIN o LEFT JOIN
	ON p.puestoid = e.puestoid
	ORDER BY e.puestoid ASC
```

## TIPO DE RELACIONES: 

*- Relacion uno a uno: Un pasajero solo tiene un pasaporte y un pasaporte pertenece a un solo pasajero.

*- Relacion de uno a muchos: Un cliente puede tener muchos pedidos, y un pedido solo pertenece a un cliente

*- Relacion de muchos a muchos: Un alumno puede tener muchos profesores y un profesor puede tener muchos alumnos 

*- En este ejemplo usaremos relacion uno a uno, con dos tablas la tabla estudiante y la tabla infoestudiantes, en la tabla estudiantes a la primera conlumna idestudiante le agregamos la PRIMARY KEY que funciona para que podamos tener id unicos y no se puedan repetir, en la tabla infoestudiantes, tambien ponemos PRIMARY KEY en su primera columna, y tambien le agregamos un CONSTRAINT que significa restrinccion, al CONSTRAINT le ponemos asi CONSTRAINT fk que significa FOREIGN KEY, mas la llave foranea que queremos poner en este caso la primera columna, luego ponemos FOREIGN KEY y su primera columna o la que vamos a poner en este caso (id_estudiante) luego hacemos referencia a la tabla que queremos poner en este caso la primera tabla que es estudiante REFERENCES estudiantes mas la columna a la que vamos hacer la llave foranea:

```
  CREATE TABLE estudiantes(
  idestudiante INTEGER PRIMARY KEY,
  apellidos VARCHAR(45),
  nombre VARCHAR(45)
  );
```
```
  CREATE  TABLE infoestudiantes(
  id_estudiante INTEGER PRIMARY KEY,
  ciudad VARCHAR(45),
	telefono VARCHAR(12),
	  CONSTRAINT FK_id_estudiante FOREIGN KEY (id_estudiante)
    REFERENCES estudiantes(idestudiante)
  );5
```

*- Cuando hacemos este registro de llave foranes y PRIMARY KEY no podemos agregar una inserccion a la tabla donde tenga un id repetido porque estaria violando la primary key y nos daria un error, tampoco podemos agregrar una inserccion a la tabla infoestudiantes sin antes hacerla en la tabla estudiantes ya que estariamos violando la llave foranea, por eso hay que hacerlo de este modo, te lo explicare en el siguiente ejemplo:

  
- Primera tabla para la inserccion 
  INSERT INTO estudiantes (idestudiante,apellidos,nombre)
  VALUES (8,'Todo poderoso', 'Dios')

-	Segunda tabla para la inserccion 
  INSERT INTO infoestudiantes (id_estudiante, ciudad, telefono)
  VALUES (8,'Universo', '100000')

## CLASE DE ALTER:

*- En este ejemplo usaremos ALTER para cambiarle el nombre a la tabla, ya que ALTER es para modificar datos, te lo mostrare en el siguiente ejemplo:

```
  ALTER TABLE infoestudiantes RENAME TO informacionAlumnos
```

*- En este ejemplo usaremos ALTER para cambiarle el nombre a una columna. te lo mostrare en el siguiente ejemplo

```
  ALTER TABLE editorial RENAME COLUMN nombre TO nombreeditorial
```

*- En este ejemplo usaremos ALTER  para añadir una nueva columna, te lo mostrare en el siguiente ejemplo

```
  ALTER TABLE informacionalumnos ADD clumnaprueba VARCHAR (45)
```

 *O DE ESTE MODO*

```
  ALTER TABLE informacionalumnos ADD COLUMN nuevacolumna VARCHAR (40)
```

*- En este ejemplo usaremos ALTER para borrar una o mas columnas de una tabla, te lo mostrare en el siguiente ejemplo: 

```
  ALTER TABLE informacionalumnos DROP COLUMN clumnaprueba
```

*- En este ejemplo usaremos ALTER para eliminar dos o mas tablas:

```
  ALTER TABLE informacionalumnos DROP COLUMN clumnaprueba DROP COLUMN nuevacolumna
```

*- En este ejemplo usaremos ALTER con ADD PRIMARY KEY para agregar la llave primaria a la columna id_estudiante, te lo mostrare en el siguiente ejemplo

```
  ALTER TABLE informacionalumnos ADD PRIMARY KEY (id_estudiante)
```

*- En este ejemplo usaremos ALTER con ADD FOREIGN KEY para agregar la llave foranea a la columna id_estudiante de la tabla informacionestudiantes y luego le hacemos una referencia (REFERENCES) a la tabla estudiantes con la columna idestudiantes 

```
  ALTER TABLE informacionalumnos ADD FOREIGN KEY (id_estudiante) 
	REFERENCES estudiantes (idestudiante)
```

## CLASE DE JOINS CON GROUP BY:

*- En este ejemplo usaremos JOINS CON GROUP BY para saber cuantos libros tenemos por editorial, te lo mostrare en el siguiente ejemplo:

```
	SELECT e.nombreeditorial,COUNT (*)
	FROM editorial e
	INNER JOIN libros l
	ON e.codigo_editorial = l.codigoeditorial
	GROUP BY e.nombreeditorial
```

## CREAR TABLA A PARTIR DE OTRA CON CREATE SELECT:

 *- En este ejemplo crearemos una tabla usando otra, le damos crear la tabla que queremos y obligatoriamente debemos ponerle AS del alias para poder crear la tabla, tendremos que usar el SELECT DISTINCT y poner el nombre de la columna en este caso puesto y luego decir de cual tabla queremos crear la otra tabla en este caso FROM empleados

```
  CREATE TABLE puestos 
	AS SELECT DISTINCT puesto
	FROM empleados
```

*- En este ejemplo te mostrare otra forma de como crear un tabla usando otra tabla, RECORDAR que el AS SELECT es para poner las columnas de la tabla que queremos usar o sea FROM empleados, te lo mostrare en el siguiente ejemplo:

```
  CREATE TABLE otraForma
	AS SELECT nombre,edad,sueldo
	FROM empleados
```

*- En este ejemplo te mostrare como crear una tabla a partir de otra tabla seleccionando solo algunos campos y donde usamos WHERE para pedir que solo lo que tengan sueldo mayor a 550 son los que va a tomar de esa tabla de empleados 

```
  CREATE TABLE rangoA 
	AS SELECT nombre, edad, sueldo 
	FROM empleados 
	WHERE sueldo > 550
```

## CREAR TABLA A PARTIR DE OTRAS NO DE OTRA, SI NO DE OTRAS, USANDO JOINS: 

*- En este ejemplo usaremos COUNT para tener un conteo del num_sucursal y le ponemos de alias AS cantidadporsucursal, recordar poner el GROUP BY con lo que pusimos dentro del parentesis del COUNT, este QUERY veremos cuantos del num_sucursal se repiten con el COUNT Y GROUP BY, ejemplo si del num_sucursal 1 hay 2 o 3 

```
	CREATE TABLE cantidasucursal
	AS SELECT v.num_sucursal,
	COUNT (v.num_sucursal) AS cantidadporSucursal
	FROM vendedor v 
	JOIN sucursales s 
	ON v.num_sucursal = s.numsucursal
	GROUP BY v.num_sucursal 
	ORDER BY v.num_sucursal ASC
```
