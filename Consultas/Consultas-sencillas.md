## Consulta 1
Mostrar los departamentos de los `tecnicos`
```sql
SELECT DISTINCT departemento FROM tecnico ;
```
Resultado:
```
areaproducion2=# SELECT DISTINCT departemento FROM tecnico ;
 departemento
--------------
 Decorados
 Sonido
 Montaje
 Video
 Iluminacion
(5 rows)
```

## Consulta 2
Mostrar los nombres de los empleados del `catering` de forma ascendente de sus fechas de ingreso
```sql
 SELECT nombre, fecha_ing FROM empleado ORDER BY fecha_ing ASC;
```
Resultado:
```
areaproducion2=# SELECT nombre, fecha_ing FROM empleado ORDER BY fecha_ing ASC;
        nombre        | fecha_ing
----------------------+------------
 Machin, Teresa       | 1968-01-15
 Viejo ,Francisco     | 1970-02-15
 Palacios, Antonio    | 1976-03-18
 Albadalejo, Cristina | 1979-01-22
 Merchan, Juan        | 1982-02-11
 Quintas, Martin      | 1986-02-04
 Merida, Luis         | 1988-02-14
 Lorite, Julian       | 1988-10-01
 Fernadez, Maria      | 1988-11-11
 Pradas, Luisa        | 1989-02-01
 Tornero, Ana         | 1991-01-15
 Tirado, Santiago     | 1992-03-01
 Barbera, Andres      | 1994-09-10
 Ribera, Carla        | 1996-01-11
 Milan, Marco         | 1996-02-28
 Vega, Roberto        | 1996-02-28
 Deniz, Adrian        | 1996-02-28
 Wang, Eva            | 1996-10-08
 Guerrero, Antonia    | 1997-01-01
 Garcia, Carmen       | 1997-01-20
 Landa, Aurora        | 1997-11-01
 Olivera, Carolina    | 1998-01-01
 Pozo, Daniel         | 1998-01-01
 Mato, Paula          | 1998-01-21
 Callejas, Manuel     | 1998-02-05
 Perez, Irene         | 1998-10-10
 Sancho, Nuria        | 1998-10-13
 Buendia, Hugo        | 1998-11-19
 Carrillo, Angeles    | 1998-11-19
(29 rows)
```

## Consulta 3
Mostrar los nombres y el DNI de los tecnicos de el equipo tecnico Los Tecnicos.
```sql
SELECT nombre, dni FROM tecnico WHERE nombre_equipotecnico = 'Los Tecnicos';
```
Resultado:
```
areaproducion2=# SELECT nombre, dni FROM tecnico WHERE nombre_equipotecnico = 'Los Tecnicos';
       nombre       |    dni
--------------------+-----------
 Portela, Zaira     | 84946524A
 Rebollo, Olivia    | 54867328T
 Aparicio, Adelina  | 73139661Y
 Perz, Javier       | 85763924Y
 Martinez, Tomas    | 46613901P
 Montes, Luis Angel | 15696504Q
 Vicente, Carlos    | 76034269H
 Alcazar, Alicia    | 42836567X
 Real, Violeta      | 10319604X
 Vazquez, Maria     | 95409569A
(10 rows)
```

## Consulta 4
Mostrar los `empleados` que sean Camareros;
```sql
SELECT * FROM empleado WHERE puesto = 'Camarero';
```
Resultado:
```
areaproducion2=# SELECT * FROM empleado WHERE puesto = 'Camarero';
  puesto  |      nombre      | id | fecha_nac  | fecha_ing  | salario | telefono  | id_catering |    dni
----------+------------------+----+------------+------------+---------+-----------+-------------+-----------
 Camarero | Quintas, Martin  | 18 | 1962-02-26 | 1986-02-04 |    1150 | 845382488 |           1 | 27432782S
 Camarero | Tirado, Santiago | 36 | 1968-08-19 | 1992-03-01 |    1150 | 782451267 |           1 | 92466798J
 Camarero | Barbera, Andres  | 38 | 1959-04-13 | 1994-09-10 |    1150 | 678456723 |           1 | 72097409E
 Camarero | Garcia, Carmen   | 42 | 1977-06-22 | 1997-01-20 |    1150 | 756345921 |           1 | 17998755J
 Camarero | Sancho, Nuria    | 62 | 1978-07-14 | 1998-10-13 |    1150 | 756449046 |           1 | 87905553J
(5 rows)
```

## Consulta 5
Mostrar el nombre y el salario de los `empleados` que ganan mas de 2000 euros
```sql
SELECT nombre, salario FROM empleado WHERE salario > 2000;
```
```
areaproducion2=# SELECT nombre, salario FROM empleado WHERE salario > 2000;
     nombre     | salario
----------------+---------
 Lorite, Julian |    2500
 Pradas, Luisa  |    2100
(2 rows)
```

## Consulta 6
Mostrar el nombre y el DNI de los `tecnicos` que la letra de su DNI sea la P.  
```sql
SELECT nombre, dni FROM tecnico WHERE dni LIKE '%P';
```
Resultado:
```
areaproducion2=# SELECT nombre, dni FROM tecnico WHERE dni LIKE '%P';
     nombre      |    dni
-----------------+-----------
 Martinez, Tomas | 46613901P
(1 row)
```

## Consulta 7
Mostrar los el nombre y el tipo de los `platos` que empiecen por la letra 'L' y sean del menu Cerrado
```sql
SELECT nombre, tipo FROM platos WHERE nombre LIKE 'L%' AND tipo = 'Cerrado';
```
Resultado:
```
areaproducion2=# SELECT nombre, tipo FROM platos WHERE nombre LIKE 'L%' AND tipo = 'Cerrado';
       nombre       |  tipo
--------------------+---------
 Lentejas con arroz | Cerrado
(1 row)
```

## Consulta 8
Mostrar los empleados en orden ascendente por el salario y en forma descendente por la fecha de ingreso
```sql
 SELECT * FROM empleado ORDER BY salario ASC, fecha_ing DESC ;
```
Resultado:
```
areaproducion2=# SELECT * FROM empleado ORDER BY salario ASC, fecha_ing DESC ;
       puesto       |        nombre        | id | fecha_nac  | fecha_ing  | salario | telefono  | id_catering |    dni
--------------------+----------------------+----+------------+------------+---------+-----------+-------------+-----------
 Ayudante repostero | Pozo, Daniel         | 50 | 1974-06-06 | 1998-01-01 |    1100 | 763379346 |           1 | 48911266H
 Segundo de cocina  | Landa, Aurora        | 64 | 1979-08-18 | 1997-11-01 |    1100 | 672654791 |           1 | 13130530Z
 Segundo de cocina  | Guerrero, Antonia    | 48 | 1975-10-08 | 1997-01-01 |    1100 | 638938645 |           1 | 87133432W
 Segundo de cocina  | Fernadez, Maria      | 10 | 1959-07-09 | 1988-11-11 |    1100 | 660439174 |           1 | 50539486E
 Camarero           | Sancho, Nuria        | 62 | 1978-07-14 | 1998-10-13 |    1150 | 756449046 |           1 | 87905553J
 Camarero           | Garcia, Carmen       | 42 | 1977-06-22 | 1997-01-20 |    1150 | 756345921 |           1 | 17998755J
 Camarero           | Barbera, Andres      | 38 | 1959-04-13 | 1994-09-10 |    1150 | 678456723 |           1 | 72097409E
 Camarero           | Tirado, Santiago     | 36 | 1968-08-19 | 1992-03-01 |    1150 | 782451267 |           1 | 92466798J
 Camarero           | Quintas, Martin      | 18 | 1962-02-26 | 1986-02-04 |    1150 | 845382488 |           1 | 27432782S
 Lavaplatos         | Carrillo, Angeles    | 60 | 1976-10-22 | 1998-11-19 |    1300 | 625894671 |           1 | 77560071T
 Lavaplatos         | Callejas, Manuel     | 34 | 1977-12-25 | 1998-02-05 |    1300 | 675463448 |           1 | 36342406Z
 Lavaplatos         | Deniz, Adrian        | 52 | 1975-04-04 | 1996-02-28 |    1300 | 631635189 |           1 | 29905642F
 Lavaplatos         | Palacios, Antonio    | 12 | 1954-10-18 | 1976-03-18 |    1300 | 646352549 |           1 | 58420478I
 Lavaplatos         | Machin, Teresa       |  8 | 1950-08-10 | 1968-01-15 |    1300 | 635646854 |           1 | 00617016H
 Repostero          | Buendia, Hugo        | 58 | 1977-02-26 | 1998-11-19 |    1500 | 673561494 |           1 | 61003945X
 Repostero          | Perez, Irene         | 40 | 1978-10-29 | 1998-10-10 |    1500 | 612646890 |           1 | 87956927M
 Cocinero           | Mato, Paula          | 44 | 1980-01-10 | 1998-01-21 |    1650 | 754784920 |           1 | 17553348R
 Cocinero           | Olivera, Carolina    | 68 | 1978-03-30 | 1998-01-01 |    1650 | 687464690 |           1 | 16145492K
 Cocinero           | Wang, Eva            | 66 | 1976-02-19 | 1996-10-08 |    1650 | 654278560 |           1 | 97380934S
 Cocinero           | Vega, Roberto        | 56 | 1976-09-26 | 1996-02-28 |    1650 | 783576389 |           1 | 75844974J
 Cocinero           | Milan, Marco         | 54 | 1976-10-21 | 1996-02-28 |    1650 | 745619086 |           1 | 22831533P
 Cocinero           | Ribera, Carla        | 46 | 1976-05-04 | 1996-01-11 |    1650 | 637920812 |           1 | 25221607Z
 Cocinero           | Tornero, Ana         | 32 | 1966-11-21 | 1991-01-15 |    1650 | 683904267 |           1 | 18071666Z
 Cocinero           | Merida, Luis         | 30 | 1967-11-30 | 1988-02-14 |    1650 | 673923571 |           1 | 50343535P
 Cocinero           | Merchan, Juan        | 14 | 1952-05-12 | 1982-02-11 |    1650 | 762103554 |           1 | 98916944Q
 Cocinero           | Albadalejo, Cristina | 16 | 1960-09-28 | 1979-01-22 |    1650 | 740901424 |           1 | 93846625R
 Cocinero           | Viejo ,Francisco     |  2 | 1949-10-11 | 1970-02-15 |    1650 | 645348096 |           1 | 31890957P
 Jefe de catering   | Pradas, Luisa        |  6 | 1965-09-09 | 1989-02-01 |    2100 | 608661593 |           1 | 93788700J
 Jefe de cocina     | Lorite, Julian       |  4 | 1955-06-09 | 1988-10-01 |    2500 | 658846977 |           1 | 19426279L
(29 rows)
```

## Consulta 9 
Mostrar el salario maximo de la tabla empleado
```sql
SELECT MIN (salario) FROM empleado ;
```
Resultado:
```
areaproducion2=# SELECT MIN (salario) FROM empleado ;
 min
------
 1100
(1 row)
```

## Consulta 10
Mostrar el salario maximo de la tabla empleado
```sql
SELECT MAX (salario) FROM empleado ;
```
Resultado:
```
areaproducion2=# SELECT MAX (salario) FROM empleado ;
 max
------
 2500
(1 row)
```

## Consulta 11
Mostrar los `materiales` ordenados de forma ascendente por su precio
```sql
SELECT nombre, precio FROM materiales ORDER BY precio ASC;
```
Resultado:
```
areaproducion2=# SELECT nombre, precio FROM materiales ORDER BY precio ASC;
                   nombre                    | precio
---------------------------------------------+--------
 BNC Macho, (Cables)                         |      3
 PROCAB HDMI, (Cables)                       |      4
 Fotomural, (Spray)                          |     16
 XLR Hembra (Cables)                         |     20
 Mark SH, (Microfono)                        |     22
 Adam Hall, (Soporte de iluminacion)         |     29
 Bote de pintura, (pintura)                  |     39
 Caja Zenture  (pintura para paaredes)       |     39
 Beamz Strobo, (Estroboscopios)              |     45
 Skytec, (Microfono de mano)                 |     47
 Banco corrido, (Gradas)                     |    103
 Pro Light Kontrak, (Control de Iluminacion) |    135
 Nicoflex Barandilla (Barandilla)            |    141
 Mixars Cut, (Mesa de mezclas)               |    169
 Mackie Pro, (Mesa de mezclas)               |    248
 WORK Pro, (Altavoz)                         |    249
 Stage Line, (Set de focos)                  |    268
 BLACKMAGIC, (Mezclador de Video)            |    905
 Roland, (Mezclador de Video)                |   2516
 JVC GY-HM89 Camcorder ,(Camara)             |   7595
 Sony HXC Studio Camera ,(Camara)            |  12065
(21 rows)
```

## Consulta 12
Mostrar los id de los `camerinos` que tengan capacidad para mas de 10 personas
```sql
 SELECT id FROM camerino WHERE capacidad LIKE  '1%';
```
Resultado:
```
areaproducion2=# SELECT id FROM camerino WHERE capacidad LIKE  '1%';
  id
------
 2001
 2002
 2003
 2004
 2007
(5 rows)
```

## Consulta 13
Mostrar el salario de los empleados que trabajan de lavaplatos
```sql
 SELECT DISTINCT puesto, salario FROM empleado WHERE puesto = 'Lavaplatos';
 ```
Resultado:
```
areaproducion2=# SELECT DISTINCT puesto, salario FROM empleado WHERE puesto = 'Lavaplatos';
   puesto   | salario
------------+---------
 Lavaplatos |    1300
(1 row)
```