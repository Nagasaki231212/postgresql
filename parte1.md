# Curso de postgresql de youtube

## CREACION DE TABLA:

*- Creamos una base de datos desde la interfaz y le colocamos de nombre "CursoYotube", luego creamos una tabla desde la herramienta de consulta con este Query 

CREATE TABLE empleados(
numempleado INTEGER,
nombre VARCHAR(45),
apellidopaterno VARCHAR(45),
apellidomaterno VARCHAR(45),
fechanacimiento DATE,
sueldo DECIMAL (7,2),
puesto VARCHAR (45)
);

## SELECT * FROM:

*- Usamos SELECT * FROM para consultar la informacion de la tabla que hemos creado:

SELECT * FROM empleados

## TIPOS DE DATOS:

*Los Tipos de datos son* :
- INTEGER: es para numeros enteros 
- VARCHAR: para texto
- DATE: para fechas
- DECIMAL: para numeros decimales
- BIGINT : numero entero mas grande

## CLASE INSERT INTO:

*- Para poder insertar datos en una tabla usamos este Query:

INSERT INTO empleado

*- Pero aqui esta el ejemplo completo:

	INSERT INTO empleados
  (numempleado, nombre, apellidopaterno, apellidomaterno, fechanacimiento, sueldo, puesto)
   VALUES (1, 'Juan Jose', 'Lopez', 'Sanchez', '1992-07-28', 4250.80, 'Contador')
  (2, 'Ana Maria', 'Gonzales', 'Miranda', '1988-05-25', 3845.2, 'Secretaria')
  (3, 'Dniel', 'Garza', 'Lopez', '1991-02-18', 6000, 'Gerente'); 

## NUEVA CLASE DE SELECT * FROM:

*- Para ver datos especificos de la tabla usamos el Query de este modo:

	SELECT nombre, sueldo, puesto FROM empleados;

*- El comando WHERE nos ayuda a filtrar la informacion o sea ver la informacion que a nosotros nos convenga en ese momento, aqui un ejemplo 
aqui podemos ver que seleccionamos toda la informacion de la tabla alumnos y le decimos con where que busque un promedio mayor o igual a 95 

	SELECT * FROM alumnos WHERE promedio >=95;

*- En este ejemplo podemos ver como solo llamo datos especificos de la tabla alumnos usando WHERE;

	SELECT nombre,carrera,promedio FROM alumnos WHERE promedio >= 100;

*- En este ejemplo usaremos WHERE y operadores relacionales aqui el ejemplo con el operador AND este obliga que se cumplan las 2 condiciones:

	SELECT * FROM alumnos WHERE promedio >= 90 AND carrera='Medicina'

*- En este ejemplo usaremos el operador OR:

	SELECT * FROM alumnos WHERE carrera='Ingenieria en Sistemas' OR carrera='Contabilidad' 

*- En este ejemplo usaremos la condicion WHERE y operadores logicos como AND y OR:

	SELECT * FROM alumnos WHERE promedio <90 AND carrera='Ingenieria en Sistemas' OR carrera='Medicina'

*- En este ejemplo usaremos la condicion WHERE con el operador NOT, NOT es para no ver un dato en especifico, te lo mostrare en este ejemplo:

	SELECT * FROM alumnos WHERE NOT carrera='ingenieria en sistemas'

## 	CLASES DE DELETE:

*- En este ejemplo usaremos DELETE, DELETE sirve para borrar datos de una tabla, en este ejemplo borraremos todos los registros de una tabla, te lo mostrare en este ejemplo:

	DELETE FROM clientes; 

*- En este ejemplo usaremos DELETE con la condicion WHERE, te lo mostrare en este ejemplo:

	DELETE FROM alumnos WHERE numcontrol = 1000 

*- En este ejemplo usaremos DELETE con la condicion WHERE y operador logico AND, te lo mostrare en este ejemplo:

	DELETE FROM alumnos WHERE nombre='Juan' apellidopaterno='Vazquez' AND apellidomaterno='Perez'

*- En este ejemplo usaremos DELETE con la condicon WHERE y el operador < menor que, te lo mostrare en este ejemplo:

	DELETE FROM alumnos WHERE promedio <90

## CLASES DE DROP:

*- En este ejemplo veremos como borrar una tabla:

	DROP TABLE alumnos;

*- En este ejemplo usaremos if para decirle que borre la tabla si existe y si no existe nos dara un mensaje en vez de un error, te lo mostrare en este ejemplo:

	DROP TABLE IF EXISTS tabla1;

## CLASE UPDATE:

*- En este ejemplo usaremos UPDATE para actualizar datos de una tabla, te lo mostrare en este ejemplo:

	UPDATE empleados SET nombre='Juan Jose'

*- En este ejemplo usaremos UPDATE para actualizar datos especifico de una tabla usando la condicion WHERE, te lo mostrare en este ejemplo:

	UPDATE clientes SET telefono='0123' WHERE idcliente=1000;

*- En este ejemplo vamos actualizar un id donde se encontraba repetido con otro id y usaremos sus datos para actualizar el registro que queremos, te lo mostrare en este ejemplo:

	UPDATE clientes SET idcliente= 1015 WHERE nombre='Daniel' AND apellidopaterno='Esparza' AND apellidomaterno='Suarez'

*- En este ejemplo vamos actualizar dos columnas de la tabla clientes, te lo mostrare en este ejemplo:

	UPDATE clientes SET ciudad='Guadalajara', estado='Jalisco' WHERE idcliente=1000

## CLASE ORDER BY:	

*- En este ejemplo usaremos ORDER BY para ordenar de forma ascendente o descendente, te lo mostrare en este ejemplo:

	+Forma ascendente  : SELECT * FROM clientes ORDER BY totaldeuda ASC
	+Forma descendente : SELECT * FROM clientes ORDER BY totaldeuda DESC

## CLASES DE DISTINCT:

*- En este ejemplo usaremos DISTINCT para obtener valores no repetidos de una tabla, te lo mostrare en este ejemplo:

	SELECT DISTINCT totaldeuda FROM clientes

*- En este ejemplo usamos DISTINCT con ORDER BY y DESC o ASC, te lo mostrare en este ejemplo:

	SELECT DISTINCT totaldeuda FROM clientes ORDER BY totaldeuda DESC 




