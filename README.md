taller de consultas SQL

1. Lista el nombre de todos los productos que hay en la tabla producto.

select 
    p.nombre 
from 
    producto 

2. Lista los nombres y los precios de todos los productos de la tabla producto.

select 
    p.nombre, p.precio
from 
    producto


3. Lista todas las columnas de la tabla producto.

select
    p.codigo
    p.nombre
    p.precio
    p.codigo_fabricante
from
    producto

4. Lista el nombre de los productos, el precio en euros y el precio en dólares
estadounidenses (USD).

select 
    (p.precio * 0.25) as 'Euros',
    (p.precio * 0.26) as 'Dolares',
from
    producto 


5. Lista el nombre de los productos, el precio en euros y el precio en dólares
estadounidenses (USD). Utiliza los siguientes alias para las columnas: nombre
de producto, euros, dólares.

select
    (p.nombre) as 'Nombre de producto'
    (p.precio * 0.25) as 'Euros',
    (p.precio * 0.26) as 'Dolares',
from
    producto 


6. Lista los nombres y los precios de todos los productos de la tabla producto,
convirtiendo los nombres a mayúscula.

SELECT 
	UPPER(p.nombre) AS 'Nombre',
	p.precio AS 'Precio'
FROM
	producto AS p;

7. Lista los nombres y los precios de todos los productos de la tabla producto,
convirtiendo los nombres a minúscula.

SELECT 
	LOWER(p.nombre),
	p.precio
FROM
	producto AS p;

8. Lista el nombre de todos los fabricantes en una columna, y en otra columna
obtenga en mayúsculas los dos primeros caracteres del nombre del
fabricante.

SELECT
	f.nombre
	UPPER(SUBSTRING(f.nombre, 1, 2))
FROM
	fabricante AS f


9. Lista los nombres y los precios de todos los productos de la tabla producto,
redondeando el valor del precio.

SELECT 
	p.nombre,
	ROUND(p.precio)
FROM
	producto AS p;

10. Lista los nombres y los precios de todos los productos de la tabla producto,
truncando el valor del precio para mostrarlo sin ninguna cifra decimal.

SELECT 
	p.nombre,
	ROUND(p.precio)
FROM
	producto AS p;

11. Lista el identificador de los fabricantes que tienen productos en la
tabla producto.

SELECT 
	f.codigo
FROM 
	fabricante AS f,
	producto AS p
WHERE
	f.codigo = p.codigo_fabricante;

12. Lista el identificador de los fabricantes que tienen productos en la
tabla producto, eliminando los identificadores que aparecen repetidos.

SELECT DISTINCT
    p.codigo_fabricante
FROM 
    producto AS p;

13. Lista los nombres de los fabricantes ordenados de forma ascendente.

SELECT 
    f.nombre
FROM 
    fabricante AS f
ORDER BY
	f.nombre ASC;

14. Lista los nombres de los fabricantes ordenados de forma descendente.

SELECT
    f.nombre
FROM 
    fabricante AS f
ORDER BY
	f.nombre DESC;

15. Lista los nombres de los productos ordenados en primer lugar por el
nombre de forma ascendente y en segundo lugar por el precio de forma
descendente.

SELECT
    p.nombre,
    p.precio
FROM 
    producto AS p
ORDER BY
	p.nombre ASC,
	p.precio DESC;

16. Devuelve una lista con las 5 primeras filas de la tabla fabricante.

SELECT
	f.codigo,
	f.nombre
FROM
	fabricante AS f
LIMIT 5;
	

17. Devuelve una lista con 2 filas a partir de la cuarta fila de la tabla fabricante.

SELECT
	f.codigo,
	f.nombre
FROM
	fabricante AS f
LIMIT 2 OFFSET 3;

La cuarta fila también se debe incluir en la respuesta.
18. Lista el nombre y el precio del producto más barato. (Utilice solamente las
cláusulas ORDER BY y LIMIT)

SELECT
    p.nombre,
    p.precio
FROM 
    producto AS p
ORDER BY
	p.precio ASC
LIMIT 1;

19. Lista el nombre y el precio del producto más caro. (Utilice solamente las
cláusulas ORDER BY y LIMIT)

SELECT
    p.nombre,
    p.precio
FROM 
    producto AS p
ORDER BY
	p.precio DESC
LIMIT 1;

20. Lista el nombre de todos los productos del fabricante cuyo identificador de
fabricante es igual a 2.

SELECT
    p.nombre,
    p.precio
FROM 
    producto AS p
WHERE
	p.codigo_fabricante = 2;

21. Lista el nombre de los productos que tienen un precio menor o igual a 120€.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	p.precio <= 120;

22. Lista el nombre de los productos que tienen un precio mayor o igual a 400€.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	p.precio >= 400;

23. Lista el nombre de los productos que no tienen un precio mayor o igual a
400€.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	p.precio < 400;

24. Lista todos los productos que tengan un precio entre 80€ y 300€. Sin utilizar
el operador BETWEEN.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	p.precio BETWEEN 80 AND 300;

25. Lista todos los productos que tengan un precio entre 60€ y 200€. Utilizando
el operador BETWEEN.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	p.precio BETWEEN 60 AND 200;

26. Lista todos los productos que tengan un precio mayor que 200€ y que el
identificador de fabricante sea igual a 6.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	(p.precio > 200) AND (p.codigo_fabricante = 6);

27. Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5.
Sin utilizar el operador IN.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	p.codigo_fabricante IN (1, 3, 5);

28. Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5.
Utilizando el operador IN.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE
	p.codigo_fabricante IN (1, 3, 5);

29. Lista el nombre y el precio de los productos en céntimos (Habrá que
multiplicar por 100 el valor del precio). Cree un alias para la columna que
contiene el precio que se llame céntimos.

SELECT
    p.nombre
    (P.precio * 100) AS 'centimos'
FROM 
    producto AS p;

30. Lista los nombres de los fabricantes cuyo nombre empiece por la letra S.

SELECT
	f.nombre
FROM
	fabricante AS f
WHERE
	f.nombre LIKE 'S%';

31. Lista los nombres de los fabricantes cuyo nombre termine por la vocal e.

SELECT
	f.nombre
FROM
	fabricante AS f
WHERE
	f.nombre LIKE '%e';

32. Lista los nombres de los fabricantes cuyo nombre contenga el carácter w.

SELECT
	f.nombre
FROM
	fabricante AS f
WHERE
	f.nombre LIKE '%w%';

33. Lista los nombres de los fabricantes cuyo nombre sea de 4 caracteres.

SELECT
	f.nombre
FROM
	fabricante AS f
WHERE
	LENGTH(f.nombre) = 4;

34. Devuelve una lista con el nombre de todos los productos que contienen la
cadena Portátil en el nombre.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE 
	p.nombre LIKE '%Portatil%';

35. Devuelve una lista con el nombre de todos los productos que contienen la
cadena Monitor en el nombre y tienen un precio inferior a 215 €.

SELECT
    p.nombre
FROM 
    producto AS p
WHERE 
	(p.nombre LIKE '%Monitor%') AND (p.precio < 215);

36. Lista el nombre y el precio de todos los productos que tengan un precio
mayor o igual a 180€. Ordene el resultado en primer lugar por el precio (en
orden descendente) y en segundo lugar por el nombre (en orden
ascendente).

SELECT
    p.nombre,
    p.precio
FROM 
    producto AS p
WHERE 
	p.precio >= 180
ORDER BY
	p.precio DESC,
	p.nombre ASC;

Consultas multitabla (Composición interna)
Resuelva todas las consultas utilizando la sintaxis de SQL1 y SQL2.

1. Devuelve una lista con el nombre del producto, precio y nombre de
fabricante de todos los productos de la base de datos.

SELECT
    p.nombre,
    p.precio,
    f.nombre AS "Nombre Fabricante"
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo

2. Devuelve una lista con el nombre del producto, precio y nombre de
fabricante de todos los productos de la base de datos. Ordene el resultado
por el nombre del fabricante, por orden alfabético.

SELECT
    p.nombre,
    p.precio,
    f.nombre AS "Nombre Fabricante"
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
ORDER BY
	f.nombre ASC;

3. Devuelve una lista con el identificador del producto, nombre del producto,
identificador del fabricante y nombre del fabricante, de todos los productos
de la base de datos.

SELECT
	p.codigo,
    p.nombre,
    f.codigo AS 'Codigo Fabricante',
    f.nombre AS "Nombre Fabricante"
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo;

4. Devuelve el nombre del producto, su precio y el nombre de su fabricante,
del producto más barato.

SELECT
	p.nombre,
    p.precio,
    f.nombre AS "Nombre Fabricante"
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
ORDER BY
	p.precio ASC
LIMIT 1;

5. Devuelve el nombre del producto, su precio y el nombre de su fabricante,
del producto más caro.

SELECT
	p.nombre,
    p.precio,
    f.nombre AS "Nombre Fabricante"
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
ORDER BY
	p.precio DESC
LIMIT 1;

6. Devuelve una lista de todos los productos del fabricante Lenovo.

SELECT
	p.nombre
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
WHERE
	f.nombre = 'Lenovo';

7. Devuelve una lista de todos los productos del fabricante Crucial que tengan
un precio mayor que 200€.

SELECT
	p.nombre
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
WHERE
	f.nombre = 'Crucial' AND p.precio > 200;

8. Devuelve un listado con todos los productos de los
fabricantes Asus, Hewlett-Packardy Seagate. Sin utilizar el operador IN.

SELECT
	p.nombre
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
WHERE
	f.nombre = 'ASUS' 
OR 
	f.nombre = 'Hewlett-Packardy'
OR 
	f.nombre = 'Seagate';

9. Devuelve un listado con todos los productos de los
fabricantes Asus, Hewlett-Packardy Seagate. Utilizando el operador IN.

SELECT
	p.nombre
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
WHERE
	f.nombre IN ('Asus', 'Hewlett-Packardy', 'Seagate');

10. Devuelve un listado con el nombre y el precio de todos los productos de los
fabricantes cuyo nombre termine por la vocal e.

SELECT
	p.nombre,
	p.precio
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
WHERE
	f.nombre LIKE '%e';

11. Devuelve un listado con el nombre y el precio de todos los productos cuyo
nombre de fabricante contenga el carácter w en su nombre.

SELECT
	p.nombre,
	p.precio
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
WHERE
	f.nombre LIKE '%w%';

12. Devuelve un listado con el nombre de producto, precio y nombre de
fabricante, de todos los productos que tengan un precio mayor o igual a
180€. Ordene el resultado en primer lugar por el precio (en orden
descendente) y en segundo lugar por el nombre (en orden ascendente)

SELECT
	p.nombre,
	p.precio,
	f.nombre AS 'Nombre Fabricante'
FROM 
    producto AS p
INNER JOIN 
	fabricante AS f
ON
	p.codigo_fabricante = f.codigo
WHERE
	p.precio >= 180
ORDER BY
	p.precio DESC,
	p.nombre ASC;

13. Devuelve un listado con el identificador y el nombre de fabricante,
solamente de aquellos fabricantes que tienen productos asociados en la
base de datos.


SELECT DISTINCT
	f.codigo,
	f.nombre AS 'Nombre Fabricante'
FROM 
    fabricante AS f
INNER JOIN 
	producto AS p
ON
	p.codigo_fabricante = f.codigo
