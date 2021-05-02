# DIAGRAMA BBDD

- Dada la siguiente descripción de tablas:

### Tabla Catering
    Telefono --- Alfanuemrico de 9 caracteres
    Nombre --- Alfanumerico de 40 caracteres
    ID --- Numerico de 5 caracteres
    Direccion --- Alfanumerico de 40 caracteres.

### Tabla Menu
    Nombre --- Alfanumerico de 40 caracteres
    Tipo --- Alfanumerico de 40 caracteres
    ID --- Alfanumerico de 5 caracteres

### Tabla Platos
    Nombre --- Alfanumerico de 40 caracteres
    Tipo --- Alfanumerico de 40 caracteres
    ID --- Alfanumerico de 5 caracteres

### Empleados
    DNI --- Alfanumerico de 9 caracteres
    Puesto --- Alfanumnerico de 20 caracteres
    Nombre --- Alfanumerico de 50 caracteres
    ID --- Alfanumerico de 5 caracteres
    Fecha_nac --- Tipo fecha
    Fecha_ing --- tipo fecha
    Salario --- Numerico de 5 posiciones
    Telefono --- Alfanumerico de 9 caracteres

### Equipo Tecnico
    Nombre --- Alfanumerico de 20 caracteres
    Telefono --- Alfanumerido de 9 caracteres

### Tecnicos
    Nombre --- Alfanumerico de 20 caracteres
    Telefono --- Alfanumerico de 9 caracteres
    DNI -- Alfanumerico de 9 caracteres
    Departemento --- Alfanuemrico de 20 caracteres
    ID --- Alfanumerico de 5 caracteres

###  Materiales
    Categoria --- Alfanumerico de 40 caracteres
    Precio --- Numerico de 10 posiciones
    ID --- Alfanumerico de 5 caracteres

### Espacios
    ID --- Alfanumerico de 10 caracteres
    Dimensiones --- Numerico de 40 posiciones
    Tipo --- Alfanumerico de 30 caracteres
    Localizacion --- Alfanumerico de 50 caracteres

### Camerinos
    ID --- Alfanumerico de 5 caracteres
    Inmobilario --- Alfanumerico de 30 caracteres
    Capacidad --- Alfanumerico de 20 caracteres

### Escenarios
    ID --- Alfannumerico de 5 caracteres
    Modelo --- Alfanumerico de 30 caracteres
    Superfifcie --- Alfanuemrico de 20 caracteres

### Artista
    ID --- Alfanumerico de 20 caracteres
    Nombre --- Alfanumerico de 40 caracteres
    DNI --- Alfanumerico de 9 caracteres
    genero_musical --- Alfanumerico de 30 caracteres


- Crea la tabla catering como el ID como la Primary KEY

- Crea la tabla empleados como el ID como la Primary KEY y  añade la columna ID_catering como Foreign Key referenciado a la columna ID de la tabla Catering 

- Crea la tabla menu como el ID como la Primary KEY y  añade la columna ID_catering como Foreign Key referenciado a la columna ID de la tabla Catering

- Crea la tabla platos como el ID como la Primary KEY

- Crea la tabla Equipo tecnico como el nombre como la Primary KEY y  añade la columna ID_catering como Foreign Key referenciado a la columna ID de la tabla Catering

- Crea la tabla materiales como el ID como la Primary KEY y  añade la columna nombre_equipotecnico como Foreign Key referenciado a la columna nombre de la tabla Equipo Tecnico

- Crea la tabla espacios como el ID como la Primary KEY y  añade la columna nombre_equipotecnico como Foreign Key referenciado a la columna nombre de la tabla Equipo Tecnico

- Crea la tabla artistas como el ID como la Primary KEY y  añade la columna ID_camerino como Foreign Key referenciado a la columna ID de la tabla Camerino
 
- Crea la tabla escenarios como el ID como la Primary KEY  y  añade la columna nombre_equipotecnico como Foreign Key referenciado a la columna nombre de la tabla Equipo Tecnico

- Crea la tabla Tecnicos como el ID como la Primary KEY y  añade la columna nombre_equipotecnico como Foreign Key referenciado a la columna nombre de la tabla Equipo Tecnico

