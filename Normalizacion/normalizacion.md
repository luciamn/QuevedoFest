# Normalizacion

Tabla Empleado:
```
       puesto       |        nombre        | id | fecha_nac  | fecha_ing  | salario | telefono  | id_catering |    dni
--------------------+----------------------+----+------------+------------+---------+-----------+-------------+-----------
 Cocinero           | Viejo ,Francisco     |  2 | 1949-10-11 | 1970-02-15 |    1650 | 645348096 |           1 | 31890957P
 Jefe de cocina     | Lorite, Julian       |  4 | 1955-06-09 | 1988-10-01 |    2500 | 658846977 |           1 | 19426279L
 Jefe de catering   | Pradas, Luisa        |  6 | 1965-09-09 | 1989-02-01 |    2100 | 608661593 |           1 | 93788700J
 Cocinero           | Albadalejo, Cristina | 16 | 1960-09-28 | 1979-01-22 |    1650 | 740901424 |           1 | 93846625R
 Camarero           | Quintas, Martin      | 18 | 1962-02-26 | 1986-02-04 |    1150 | 845382488 |           1 | 27432782S
 Cocinero           | Merida, Luis         | 30 | 1967-11-30 | 1988-02-14 |    1650 | 673923571 |           1 | 50343535P
 Cocinero           | Tornero, Ana         | 32 | 1966-11-21 | 1991-01-15 |    1650 | 683904267 |           1 | 18071666Z
 Lavaplatos         | Callejas, Manuel     | 34 | 1977-12-25 | 1998-02-05 |    1300 | 675463448 |           1 | 36342406Z
 Camarero           | Tirado, Santiago     | 36 | 1968-08-19 | 1992-03-01 |    1150 | 782451267 |           1 | 92466798J
 Camarero           | Barbera, Andres      | 38 | 1959-04-13 | 1994-09-10 |    1150 | 678456723 |           1 | 72097409E
 Repostero          | Perez, Irene         | 40 | 1978-10-29 | 1998-10-10 |    1500 | 612646890 |           1 | 87956927M
 Camarero           | Garcia, Carmen       | 42 | 1977-06-22 | 1997-01-20 |    1150 | 756345921 |           1 | 17998755J
 Cocinero           | Mato, Paula          | 44 | 1980-01-10 | 1998-01-21 |    1650 | 754784920 |           1 | 17553348R
 Cocinero           | Ribera, Carla        | 46 | 1976-05-04 | 1996-01-11 |    1650 | 637920812 |           1 | 25221607Z
 Segundo de cocina  | Guerrero, Antonia    | 48 | 1975-10-08 | 1997-01-01 |    1100 | 638938645 |           1 | 87133432W
 Ayudante repostero | Pozo, Daniel         | 50 | 1974-06-06 | 1998-01-01 |    1100 | 763379346 |           1 | 48911266H
 Lavaplatos         | Deniz, Adrian        | 52 | 1975-04-04 | 1996-02-28 |    1300 | 631635189 |           1 | 29905642F
 Cocinero           | Milan, Marco         | 54 | 1976-10-21 | 1996-02-28 |    1650 | 745619086 |           1 | 22831533P
 Cocinero           | Vega, Roberto        | 56 | 1976-09-26 | 1996-02-28 |    1650 | 783576389 |           1 | 75844974J
 Repostero          | Buendia, Hugo        | 58 | 1977-02-26 | 1998-11-19 |    1500 | 673561494 |           1 | 61003945X
 Lavaplatos         | Carrillo, Angeles    | 60 | 1976-10-22 | 1998-11-19 |    1300 | 625894671 |           1 | 77560071T
 Camarero           | Sancho, Nuria        | 62 | 1978-07-14 | 1998-10-13 |    1150 | 756449046 |           1 | 87905553J
 Cocinero           | Wang, Eva            | 66 | 1976-02-19 | 1996-10-08 |    1650 | 654278560 |           1 | 97380934S
 Cocinero           | Olivera, Carolina    | 68 | 1978-03-30 | 1998-01-01 |    1650 | 687464690 |           1 | 16145492K
 Lavaplatos         | Machin, Teresa       |  8 | 1950-08-10 | 1968-01-15 |    1300 | 635646854 |           1 | 00617016H
 Segundo de cocina  | Fernadez, Maria      | 10 | 1959-07-09 | 1988-11-11 |    1100 | 660439174 |           1 | 50539486E
 Lavaplatos         | Palacios, Antonio    | 12 | 1954-10-18 | 1976-03-18 |    1300 | 646352549 |           1 | 58420478I
 Cocinero           | Merchan, Juan        | 14 | 1952-05-12 | 1982-02-11 |    1650 | 762103554 |           1 | 98916944Q
 Segundo de cocina  | Landa, Aurora        | 64 | 1979-08-18 | 1997-11-01 |    1100 | 672654791 |           1 | 13130530Z
(29 rows)
```
¿Primera forma normal?
Si, porque no contiene ningun atributo multivalor
¿Segunda forma normal?
Veamos las dependecias funcionales
DNI --> nombre, fecha_nac, telefono
puesto, fecha_ing, salario, id_catering --> id