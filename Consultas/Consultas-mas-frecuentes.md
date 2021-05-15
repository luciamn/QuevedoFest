## Consulta 1
Mostrar toda la información de la tabla `Tecncicos`.
```sql
SELECT * FROM tecnico ;
```
Resultado:
```
areaproducion2=# SELECT * FROM tecnico ;
         nombre          | telefono  |    dni    | departemento | id  | nombre_equipotecnico
-------------------------+-----------+-----------+--------------+-----+----------------------
 Blanco, Gabriela        | 672563509 | 08972215F | Iluminacion  | 100 | Tecnicos Bola
 Portela, Zaira          | 637892641 | 84946524A | Montaje      | 103 | Los Tecnicos
 Rebollo, Olivia         | 618226007 | 54867328T | Sonido       | 105 | Los Tecnicos
 Rojo, Armando           | 682726789 | 21582345L | Iluminacion  | 107 | Tecnicos Bola
 GMarti, Felipe          | 674907618 | 45844648J | Sonido       | 109 | Tecnicos Bola
 Rosello, Neus           | 748236123 | 80512066Z | Video        | 111 | Tecnicos Bola
 Aparicio, Adelina       | 638940812 | 73139661Y | Decorados    | 113 | Los Tecnicos
 Perz, Javier            | 746280147 | 85763924Y | Decorados    | 115 | Los Tecnicos
 Martinez, Tomas         | 648903712 | 46613901P | Sonido       | 117 | Los Tecnicos
 Zamorano, Antonio Jesus | 643924783 | 66555102W | Sonido       | 119 | Tecnicos Bola
 Ojeda, Nicolas          | 673982456 | 49609409L | Iluminacion  | 121 | Tecnicos Bola
 Montes, Luis Angel      | 748092571 | 15696504Q | Iluminacion  | 123 | Los Tecnicos
 Vicente, Carlos         | 748290745 | 76034269H | Montaje      | 125 | Los Tecnicos
 Blanco, Gabriela        | 672981356 | 27573170B | Iluminacion  | 127 | Tecnicos Bola
 Blanco, Gabriela        | 712948354 | 47046860S | Sonido       | 129 | Tecnicos Bola
 Alcazar, Alicia         | 601375834 | 42836567X | Decorados    | 131 | Los Tecnicos
 Montesinos, Eduardo     | 612482674 | 3634790Q  | Video        | 133 | Tecnicos Bola
 Real, Violeta           | 657290543 | 10319604X | Montaje      | 135 | Los Tecnicos
 Galiano, Carmen         | 735920864 | 48051532R | Montaje      | 137 | Tecnicos Bola
 Simon, Aroa             | 732984613 | 54430800N | Sonido       | 139 | Tecnicos Bola
 Olmedo, Pepe            | 662918461 | 89051236C | Iluminacion  | 141 | Tecnicos Bola
 Vazquez, Maria          | 739613498 | 95409569A | Video        | 143 | Los Tecnicos
 Montesinos, Eduardo     | 612482674 | 3634790Q  | Video        | 145 | Tecnicos Bola
(23 rows)
```

## Consulta 2
Mostrar los `platos` Vegetarianos.
```sql
SELECT nombre FROM platos WHERE tipo = 'Vegetariano';
```
Resultado:
```
areaproducion2=# SELECT nombre FROM platos WHERE tipo = 'Vegetariano';
    nombre
---------------
 Mac an cheese
 Falafel
 Tabaoule
(3 rows)
```

## Consulta 3
Mostrar las dimensiones de los `escenarios`
```sql
 SELECT dimensiones, tipo FROM espacio WHERE tipo = 'Escenario';
```
Resultado:
```
areaproducion2=# SELECT dimensiones, tipo FROM espacio WHERE tipo = 'Escenario';
 dimensiones |   tipo
-------------+-----------
 1370x30     | Escenario
 110x15      | Escenario
 148x35      | Escenario
 150x24      | Escenario
(4 rows)
```

## Consulta 4
Mostrar el nombre  de los `tecnicos` que trabajan en el departamento de Iluminacion.
```sql
 SELECT nombre FROM tecnico WHERE departemento = 'Iluminacion';
```
Resultado:
```
areaproducion2=# SELECT nombre FROM tecnico WHERE departemento = 'Iluminacion';
       nombre
--------------------
 Blanco, Gabriela
 Rojo, Armando
 Ojeda, Nicolas
 Montes, Luis Angel
 Blanco, Gabriela
 Olmedo, Pepe
(6 rows)
```


## Consulta 5
Mostrar los `empleados` del catering que se unieron a la empresa antes de 1980
```sql
SELECT * FROM empleado WHERE fecha_ing < '1980-01-01';
```
Resultado:
```
areaproducion2=# SELECT * FROM empleado WHERE fecha_ing < '1980-01-01';
   puesto   |        nombre        | id | fecha_nac  | fecha_ing  | salario | telefono  | id_catering |    dni
------------+----------------------+----+------------+------------+---------+-----------+-------------+-----------
 Cocinero   | Viejo ,Francisco     |  2 | 1949-10-11 | 1970-02-15 |    1650 | 645348096 |           1 | 31890957P
 Cocinero   | Albadalejo, Cristina | 16 | 1960-09-28 | 1979-01-22 |    1650 | 740901424 |           1 | 93846625R
 Lavaplatos | Machin, Teresa       |  8 | 1950-08-10 | 1968-01-15 |    1300 | 635646854 |           1 | 00617016H
 Lavaplatos | Palacios, Antonio    | 12 | 1954-10-18 | 1976-03-18 |    1300 | 646352549 |           1 | 58420478I
(4 rows)
```

## Consulta 6 
Mostrar todos los `menus`
```sql
 SELECT * FROM menu ;
```
Reultado:
```
areaproducion2=# SELECT * FROM menu ;
    nombre    |     tipo     | id | id_catering
--------------+--------------+----+-------------
 Verde        | Vegetariano  | 10 |           1
 Menores      | Infantil     | 20 |           1
 Poco         | Sencillo     | 30 |           1
 A placer     | Degustacion  | 40 |           1
 Cocina       | Gastronomico | 50 |           1
 Unica Opcion | Cerrado      | 60 |           1
 Especial     | Concertado   | 70 |           1
 Repetido     | Fijo         | 80 |           1
 Del dia      | De la casa   | 90 |           1
(9 rows)
```

## Consulta 7 
Mostrar la media de los salarios de los `empeleados` de catering
```sql
SELECT avg (salario) FROM empleado ;
```
Resultado:
```
areaproducion2=# SELECT avg (salario) FROM empleado ;
          avg
-----------------------
 1462.0689655172413793
(1 row)
```