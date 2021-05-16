# VISTAS

## Vista1 
Crea una vista llamada platos de la casa que muestre los platos del menu de la casa.
```sql
 CREATE VIEW platodelacasa AS
 SELECT nombre FROM platos WHERE tipo = 'de la casa';
```
Resultado:
```
areaproducion2=# SELECT * FROM platodelacasa ;
         nombre
-------------------------
 Ensalada Mixta
 Montadito de boquerones
 Pastel de carbacho
(3 rows)
```

## Vista 2
Crea una vista llamada material que muestre el nombre, precio y id de los materiales
```sql
CREATE VIEW material AS
 SELECT nombre, precio, id FROM materiales;
```
Resultado:
```
areaproducion2=# SELECT * FROM material;
                   nombre                    | precio | id
---------------------------------------------+--------+----
 JVC GY-HM89 Camcorder ,(Camara)             |   7595 |  2
 BLACKMAGIC, (Mezclador de Video)            |    905 |  3
 Sony HXC Studio Camera ,(Camara)            |  12065 | 23
 Roland, (Mezclador de Video)                |   2516 | 24
 Beamz Strobo, (Estroboscopios)              |     45 |  4
 Pro Light Kontrak, (Control de Iluminacion) |    135 |  5
 Stage Line, (Set de focos)                  |    268 |  6
 Adam Hall, (Soporte de iluminacion)         |     29 |  7
 WORK Pro, (Altavoz)                         |    249 |  8
 Mark SH, (Microfono)                        |     22 |  9
 Skytec, (Microfono de mano)                 |     47 | 10
 Mackie Pro, (Mesa de mezclas)               |    248 | 11
 Mixars Cut, (Mesa de mezclas)               |    169 | 12
 Banco corrido, (Gradas)                     |    103 | 13
 BNC Macho, (Cables)                         |      3 | 16
 XLR Hembra (Cables)                         |     20 | 17
 PROCAB HDMI, (Cables)                       |      4 | 18
 Nicoflex Barandilla (Barandilla)            |    141 | 19
 Fotomural, (Spray)                          |     16 | 20
 Bote de pintura, (pintura)                  |     39 | 21
 Caja Zenture  (pintura para paaredes)       |     39 | 22
(21 rows)
```
Modificamos la consulta y añadimos que nos enseñe tambien la categoria, y el nombre del equipo tecnico y que solo saque los materiales que los gestiona el equipo tecnico 'Tecnicos Bola'

```sql
CREATE OR REPLACE VIEW material AS
 SELECT nombre, precio, id, categoria, nombre_equipotecnico
  FROM materiales
 WHERE nombre_equipotecnico = 'Tecnicos Bola';
```
Resultado:
```
areaproducion2=# SELECT * FROM material;
                   nombre                    | precio | id |  categoria  | nombre_equipotecnico
---------------------------------------------+--------+----+-------------+----------------------
 Sony HXC Studio Camera ,(Camara)            |  12065 | 23 | Video       | Tecnicos Bola
 Roland, (Mezclador de Video)                |   2516 | 24 | Video       | Tecnicos Bola
 Beamz Strobo, (Estroboscopios)              |     45 |  4 | Iluminacion | Tecnicos Bola
 Pro Light Kontrak, (Control de Iluminacion) |    135 |  5 | Iluminacion | Tecnicos Bola
 Stage Line, (Set de focos)                  |    268 |  6 | Iluminacion | Tecnicos Bola
 Mark SH, (Microfono)                        |     22 |  9 | Sonido      | Tecnicos Bola
 Mixars Cut, (Mesa de mezclas)               |    169 | 12 | Sonido      | Tecnicos Bola
 BNC Macho, (Cables)                         |      3 | 16 | Montaje     | Tecnicos Bola
 XLR Hembra (Cables)                         |     20 | 17 | Montaje     | Tecnicos Bola
 PROCAB HDMI, (Cables)                       |      4 | 18 | Montaje     | Tecnicos Bola
 Fotomural, (Spray)                          |     16 | 20 | Decorado    | Tecnicos Bola
(11 rows)
```

# SECUENIAS
Creacion de la secuencia
```sql
 CREATE SEQUENCE s1
 INCREMENT 5
 START 100;
```
Nextval:
```
areaproducion2=# SELECT nextval('s1');
 nextval
---------
     100
(1 row)
```
Curval:
```
areaproducion2=# SELECT currval('s1');
 currval
---------
     100
(1 row)

```
Setval:
```
areaproducion2=# SELECT setval('s1', 200);
 setval
--------
    200
(1 row)
```
Añadimos una fila a la tabla catering
```sql
INSERT INTO catering VALUES
(nextval('s1'), 'El Trebol', 2, 'c/ Calahorra');
```
Secuencias existentes
```
areaproducion2=# \ds
          List of relations
 Schema | Name |   Type   |  Owner
--------+------+----------+----------
 public | s1   | sequence | postgres
(1 row)
```
```
areaproducion2=# \d s1
                             Sequence "public.s1"
  Type  | Start | Minimum |       Maximum       | Increment | Cycles? | Cache
--------+-------+---------+---------------------+-----------+---------+-------
 bigint |   100 |       1 | 9223372036854775807 |         5 | no      |     1
```
# Indice
creamos el indice
```sql
CREATE INDEX empleados_id_catering_ix ON empleado (id_catering);
```
Resultado:
```
areaproducion2=# \d empleado;
                       Table "public.empleado"
   Column    |         Type          | Collation | Nullable | Default
-------------+-----------------------+-----------+----------+---------
 puesto      | character varying(20) |           |          |
 nombre      | character varying(50) |           |          |
 id          | numeric(5,0)          |           | not null |
 fecha_nac   | date                  |           |          |
 fecha_ing   | date                  |           |          |
 salario     | numeric(5,0)          |           |          |
 telefono    | character varying(9)  |           |          |
 id_catering | integer               |           | not null |
 dni         | character varying(9)  |           |          |
Indexes:
    "empleado_pkey" PRIMARY KEY, btree (id)
    "empleados_id_catering_ix" btree (id_catering)
Foreign-key constraints:
    "empleados_id_catering" FOREIGN KEY (id_catering) REFERENCES catering(id)

```