## Consulta 1
Mostrar cuantos `empleados` hay en cada puesto
```sql
 SELECT puesto, COUNT(*) FROM empleado GROUP BY puesto;
``` 
Resultado:
```
areaproducion2=# SELECT puesto, COUNT(*) FROM empleado GROUP BY puesto;
       puesto       | count
--------------------+-------
 Jefe de catering   |     1
 Ayudante repostero |     1
 Cocinero           |    11
 Camarero           |     5
 Lavaplatos         |     5
 Jefe de cocina     |     1
 Repostero          |     2
 Segundo de cocina  |     3
(8 rows)
```

## Consulta 2
Mosstrar cuanto `materiales` hay en cada categoria
```sql
 SELECT categoria, COUNT(*) FROM materiales GROUP BY categoria;
```
Resultado:
```
areaproducion2=# SELECT categoria, COUNT(*) FROM materiales GROUP BY categoria;
  categoria  | count
-------------+-------
 Decorado    |     3
 Sonido      |     5
 Montaje     |     5
 Video       |     4
 Iluminacion |     4
(5 rows)
```

## Consulta 3
Mostrar el número y la suma de sus salarios de los `empleados` que son Cocineros
```sql
 SELECT COUNT(*) AS "num. empleado", SUM(salario) AS "Suma de salarios" FROM empleado WHERE puesto = 'Cocinero';
```
Resultado:
```
areaproducion2=# SELECT COUNT(*) AS "num. empleado", SUM(salario) AS "Suma de salarios" FROM empleado WHERE puesto = 'Cocinero';
 num. empleado | Suma de salarios
---------------+------------------
            11 |            18150
(1 row)
```

## Consulta 4
Mostrar el número de `empleados`, el mínimo y el máximo salario de los empleados que han ingresado en la compañía organizados por año.
```sql
SELECT TO_CHAR(fecha_ing, 'YYYY') AS "año ingreso",
    COUNT(*) "num. emp",
    MIN(salario) AS "mín. salario",
    MAX(salario) AS "máx. salario"
FROM empleado
GROUP BY "fecha_ing"
ORDER BY "fecha_ing";
```
Resultado:
```
areaproducion2=# SELECT TO_CHAR(fecha_ing, 'YYYY') AS "año ingreso",     COUNT(*) "num. emp",     MIN(salario) AS "mín. salario",     MAX(salario) AS "máx. salario" FROM empleado GROUP BY "fecha_ing" ORDER BY " fecha_ing";
 año ingreso | num. emp | mín. salario | máx. salario
-------------+----------+--------------+--------------
 1968        |        1 |         1300 |         1300
 1970        |        1 |         1650 |         1650
 1976        |        1 |         1300 |         1300
 1979        |        1 |         1650 |         1650
 1982        |        1 |         1650 |         1650
 1986        |        1 |         1150 |         1150
 1988        |        1 |         1650 |         1650
 1988        |        1 |         2500 |         2500
 1988        |        1 |         1100 |         1100
 1989        |        1 |         2100 |         2100
 1991        |        1 |         1650 |         1650
 1992        |        1 |         1150 |         1150
 1994        |        1 |         1150 |         1150
 1996        |        1 |         1650 |         1650
 1996        |        3 |         1300 |         1650
 1996        |        1 |         1650 |         1650
 1997        |        1 |         1100 |         1100
 1997        |        1 |         1150 |         1150
 1997        |        1 |         1100 |         1100
 1998        |        2 |         1100 |         1650
 1998        |        1 |         1650 |         1650
 1998        |        1 |         1300 |         1300
 1998        |        1 |         1500 |         1500
 1998        |        1 |         1150 |         1150
 1998        |        2 |         1300 |         1500
(25 rows)
```

## Consulta 5 
Mostrar cuantos `platos` tiene cada menu
```sql
SELECT tipo AS "Menu", COUNT(*) AS "plato" FROM platos GROUP BY tipo;
```
Resultado:
```
areaproducion2=# SELECT tipo AS "Menu", COUNT(*) AS "plato" FROM platos GROUP BY tipo;
     Menu     | plato
--------------+-------
 Gastronomico |     3
 Sencillo     |     3
 Infantil     |     3
 Fijo         |     3
 Concertado   |     2
 Degustacion  |     2
 Cerrado      |     3
 Vegetariano  |     3
 De la casa   |     3
(9 rows)

```

## Consulta 6
Hacer una lista que muestre los nombres de las categorias que tengan mas de 4 `materiales`
```sql
 SELECT categoria, COUNT(*) FROM materiales GROUP BY categoria HAVING COUNT(*) > 4;
```
Resultado:
```
areaproducion2=# SELECT categoria, COUNT(*) FROM materiales GROUP BY categoria HAVING COUNT(*) > 4;
 categoria | count
-----------+-------
 Sonido    |     5
 Montaje   |     5
(2 rows)
```

## Consulta 7
Mostrar el nombre, puesto, DNI y salario de los `empleados` que tienen un salario entre 900 y 1300
```sql
SELECT nombre, puesto, dni, salario FROM empleado GROUP BY nombre, puesto, dni, salario HAVING AVG(salario) BETWEEN 900 AND 1300;
```
Resultado:
```
areaproducion2=# SELECT nombre, puesto, dni, salario FROM empleado GROUP BY nombre, puesto, dni, salario HAVING AVG(salario) BETWEEN 900 AND 1300;
      nombre       |       puesto       |    dni    | salario
-------------------+--------------------+-----------+---------
 Garcia, Carmen    | Camarero           | 17998755J |    1150
 Fernadez, Maria   | Segundo de cocina  | 50539486E |    1100
 Pozo, Daniel      | Ayudante repostero | 48911266H |    1100
 Landa, Aurora     | Segundo de cocina  | 13130530Z |    1100
 Quintas, Martin   | Camarero           | 27432782S |    1150
 Guerrero, Antonia | Segundo de cocina  | 87133432W |    1100
 Palacios, Antonio | Lavaplatos         | 58420478I |    1300
 Barbera, Andres   | Camarero           | 72097409E |    1150
 Tirado, Santiago  | Camarero           | 92466798J |    1150
 Sancho, Nuria     | Camarero           | 87905553J |    1150
 Carrillo, Angeles | Lavaplatos         | 77560071T |    1300
 Machin, Teresa    | Lavaplatos         | 00617016H |    1300
 Callejas, Manuel  | Lavaplatos         | 36342406Z |    1300
 Deniz, Adrian     | Lavaplatos         | 29905642F |    1300
(14 rows)
```

## Consulta 8
Mostrar el numero de `tecnicos` que trabajan en los dos equipos tecnicos
```sql
 SELECT COUNT(*) AS "num. empleado", nombre_equipotecnico AS "Equipo Tecnico" FROM tecnico GROUP BY nombre_equipotecnico;
```
Resultado:
```
areaproducion2=# SELECT COUNT(*) AS "num. empleado", nombre_equipotecnico AS "Equipo Tecnico" FROM tecnico GROUP BY nombre_equipotecnico;
 num. empleado | Equipo Tecnico
---------------+----------------
            13 | Tecnicos Bola
            10 | Los Tecnicos
(2 rows)
```
## Consulta 10
Mostrar el numero de `artistas` que cantan cada genero
```sql
SELECT COUNT(*) AS "num. de artistas", genero_musical FROM artista GROUP BY genero_musical;
```
Resultado:
```
areaproducion2=# SELECT COUNT(*) AS "num. de artistas", genero_musical FROM artista GROUP BY genero_musical;
 num. de artistas | genero_musical
------------------+----------------
                2 | Pop
                1 | Soul
                1 | Rock
                1 | Heavy
                2 | Urbano
(5 rows)
```



## Consulta 10
Se desea realizar una estadística de las fechas de contratación de los empleados a partir del 1980. Para ello, se desea que se desglose que número de empleados ha empezado a trabajar en que año y en que mes.
```sql
SELECT TO_CHAR(fecha_ing, 'YYYY') AS año,
TO_NUMBER(TO_CHAR(fecha_ing, 'MM'), '99') AS mes,
COUNT(*) AS "num. empleado" FROM empleado WHERE fecha_ing >= '1980-01-01' GROUP BY ROLLUP (año, mes) ORDER BY año, mes;
```
Resultado:
```
areaproducion2=# SELECT TO_CHAR(fecha_ing, 'YYYY') AS año,
TO_NUMBER(TO_CHAR(fecha_ing, 'MM'), '99') AS mes,
COUNT(*) AS "num. empleado" FROM empleado WHERE fecha_ing >= '1980-01-01' GROUP BY ROLLUP (año, mes) ORDER BY año, mes;
 año  | mes | num. empleado
------+-----+---------------
 1982 |   2 |             1
 1982 |     |             1
 1986 |   2 |             1
 1986 |     |             1
 1988 |   2 |             1
 1988 |  10 |             1
 1988 |  11 |             1
 1988 |     |             3
 1989 |   2 |             1
 1989 |     |             1
 1991 |   1 |             1
 1991 |     |             1
 1992 |   3 |             1
 1992 |     |             1
 1994 |   9 |             1
 1994 |     |             1
 1996 |   1 |             1
 1996 |   2 |             3
 1996 |  10 |             1
 1996 |     |             5
 1997 |   1 |             2
 1997 |  11 |             1
 1997 |     |             3
 1998 |   1 |             3
 1998 |   2 |             1
 1998 |  10 |             2
 1998 |  11 |             2
 1998 |     |             8
      |     |            25
(29 rows)
```

## Consulta 11
Mostrar el numero de `camerinos` y `escenario` que hay en el festival
```sql
SELECT tipo, COUNT(*) FROM espacio GROUP BY tipo;
```
Resultado:
```
areaproducion2=# SELECT tipo, COUNT(*) FROM espacio GROUP BY tipo;
   tipo    | count
-----------+-------
 Camerino  |     7
 Escenario |     4
(2 rows)

```