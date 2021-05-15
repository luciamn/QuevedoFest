## Consulta 1
Nombre y puesto de los `empleados` que son reposteros
```sql
 SELECT nombre, puesto FROM empleado WHERE puesto = ALL (SELECT puesto FROM empleado WHERE puesto = 'Repostero');
```
Resultado:
```
areaproducion2=# SELECT nombre, puesto FROM empleado WHERE puesto = ALL (SELECT puesto FROM empleado WHERE puesto = 'Repostero');
    nombre     |  puesto
---------------+-----------
 Perez, Irene  | Repostero
 Buendia, Hugo | Repostero
(2 rows)
```

## Consulta 2
Mostrar los `materiales` que cuesten mas que el altavoz WORK Pro
```sql
ELECT nombre, precio FROM materiales WHERE precio > ALL (SELECT precio FROM materiales WHERE nombre = 'WORK Pro, (Altavoz)');
```
Resultado:
```
areaproducion2=# SELECT nombre, precio FROM materiales WHERE precio > ALL (SELECT precio FROM materiales WHERE nombre = 'WORK Pro, (Altavoz)');
              nombre              | precio
----------------------------------+--------
 JVC GY-HM89 Camcorder ,(Camara)  |   7595
 BLACKMAGIC, (Mezclador de Video) |    905
 Sony HXC Studio Camera ,(Camara) |  12065
 Roland, (Mezclador de Video)     |   2516
 Stage Line, (Set de focos)       |    268
(5 rows)
```
## Consulta 3
Mostrar el nombre, puesto y DNI de los `empleados` con el mismo puesto que Roberto Vega
```sql
 SELECT nombre, puesto, dni FROM empleado WHERE puesto = (SELECT puesto FROM empleado WHERE nombre = 'Vega, Roberto') AND nombre != 'Vega, Roberto';
```
Resultado:
```
areaproducion2=# SELECT nombre, puesto, dni FROM empleado WHERE puesto = (SELECT puesto FROM empleado WHERE nombre = 'Vega, Roberto') AND nombre != 'Vega, Roberto';
        nombre        |  puesto  |    dni
----------------------+----------+-----------
 Viejo ,Francisco     | Cocinero | 31890957P
 Albadalejo, Cristina | Cocinero | 93846625R
 Merida, Luis         | Cocinero | 50343535P
 Tornero, Ana         | Cocinero | 18071666Z
 Mato, Paula          | Cocinero | 17553348R
 Ribera, Carla        | Cocinero | 25221607Z
 Milan, Marco         | Cocinero | 22831533P
 Wang, Eva            | Cocinero | 97380934S
 Olivera, Carolina    | Cocinero | 16145492K
 Merchan, Juan        | Cocinero | 98916944Q
(10 rows)
```

## Consulta 4
Mostrar el nombre, genero_musical y DNI de los `artistas` con el mismo genero_musical que Julian Falcon
```sql
 SELECT nombre, genero_musical, dni FROM artista WHERE genero_musical = (SELECT genero_musical FROM artista WHERE nombre = 'Falcon, Julian') AND nombre != 'Falcon, Julian';
```
Resultado:
```
areaproducion2=# SELECT nombre, genero_musical, dni FROM artista WHERE genero_musical = (SELECT genero_musical FROM artista WHERE nombre = 'Falcon, Julian') AND nombre != 'Falcon, Julian';
     nombre     | genero_musical |    dni
----------------+----------------+-----------
 Sierrra, Josep | Urbano         | 70997897W
(1 row)
```

## Consulta 5
Mostrar a los compañeros de equipo tecnico que tiene Violeta Real
```sql
 SELECT * FROM  tecnico  WHERE nombre_equipotecnico = (SELECT nombre_equipotecnico FROM tecnico WHERE nombre = 'Real, Violeta') AND nombre != 'Real, Violeta';
```
Resultado:
```
areaproducion2=# SELECT * FROM  tecnico  WHERE nombre_equipotecnico = (SELECT nombre_equipotecnico FROM tecnico WHERE nombre = 'Real, Violeta') AND nombre != 'Real, Violeta';
       nombre       | telefono  |    dni    | departemento | id  | nombre_equipotecnico
--------------------+-----------+-----------+--------------+-----+----------------------
 Portela, Zaira     | 637892641 | 84946524A | Montaje      | 103 | Los Tecnicos
 Rebollo, Olivia    | 618226007 | 54867328T | Sonido       | 105 | Los Tecnicos
 Aparicio, Adelina  | 638940812 | 73139661Y | Decorados    | 113 | Los Tecnicos
 Perz, Javier       | 746280147 | 85763924Y | Decorados    | 115 | Los Tecnicos
 Martinez, Tomas    | 648903712 | 46613901P | Sonido       | 117 | Los Tecnicos
 Montes, Luis Angel | 748092571 | 15696504Q | Iluminacion  | 123 | Los Tecnicos
 Vicente, Carlos    | 748290745 | 76034269H | Montaje      | 125 | Los Tecnicos
 Alcazar, Alicia    | 601375834 | 42836567X | Decorados    | 131 | Los Tecnicos
 Vazquez, Maria     | 739613498 | 95409569A | Video        | 143 | Los Tecnicos
(9 rows)

```

## Consulta 7
Mostrar el nombre, dni, salario de los `empleados` que ganan mas que cualquier lavaplatos
```sql
 SELECT nombre, dni, salario FROM empleado WHERE salario > ALL (SELECT salario FROM empleado WHERE puesto = 'Lavaplatos');
```
Resultado:
```
areaproducion2=# SELECT nombre, dni, salario FROM empleado WHERE salario > ALL (SELECT salario FROM empleado WHERE puesto = 'Lavaplatos');
        nombre        |    dni    | salario
----------------------+-----------+---------
 Viejo ,Francisco     | 31890957P |    1650
 Lorite, Julian       | 19426279L |    2500
 Pradas, Luisa        | 93788700J |    2100
 Albadalejo, Cristina | 93846625R |    1650
 Merida, Luis         | 50343535P |    1650
 Tornero, Ana         | 18071666Z |    1650
 Perez, Irene         | 87956927M |    1500
 Mato, Paula          | 17553348R |    1650
 Ribera, Carla        | 25221607Z |    1650
 Milan, Marco         | 22831533P |    1650
 Vega, Roberto        | 75844974J |    1650
 Buendia, Hugo        | 61003945X |    1500
 Wang, Eva            | 97380934S |    1650
 Olivera, Carolina    | 16145492K |    1650
 Merchan, Juan        | 98916944Q |    1650
(15 rows)
```

## Consulta 8 
Mostrar que `tecnico` pertenece a que equipo tecnico
```sql
 SELECT t.nombre "tecnico", e.nombre "nombre"
FROM tecnico t  JOIN equipo_tecnico e ON (t.nombre_equipotecnico = e.nombre);
´´´
Resultado:
```
```
areaproducion2=# SELECT t.nombre "tecnico",
e.nombre "nombre"
FROM tecnico t  JOIN equipo_tecnico e ON (t.nombre_equipotecnico = e.nombre);
         tecnico         |    nombre
-------------------------+---------------
 Blanco, Gabriela        | Tecnicos Bola
 Portela, Zaira          | Los Tecnicos
 Rebollo, Olivia         | Los Tecnicos
 Rojo, Armando           | Tecnicos Bola
 GMarti, Felipe          | Tecnicos Bola
 Rosello, Neus           | Tecnicos Bola
 Aparicio, Adelina       | Los Tecnicos
 Perz, Javier            | Los Tecnicos
 Martinez, Tomas         | Los Tecnicos
 Zamorano, Antonio Jesus | Tecnicos Bola
 Ojeda, Nicolas          | Tecnicos Bola
 Montes, Luis Angel      | Los Tecnicos
 Vicente, Carlos         | Los Tecnicos
 Blanco, Gabriela        | Tecnicos Bola
 Blanco, Gabriela        | Tecnicos Bola
 Alcazar, Alicia         | Los Tecnicos
 Montesinos, Eduardo     | Tecnicos Bola
 Real, Violeta           | Los Tecnicos
 Galiano, Carmen         | Tecnicos Bola
 Simon, Aroa             | Tecnicos Bola
 Olmedo, Pepe            | Tecnicos Bola
 Vazquez, Maria          | Los Tecnicos
 Montesinos, Eduardo     | Tecnicos Bola
(23 rows)
```
