# CREACION DE TABLAS Y OTROS OBJETOS

## Creacion de Tablas

## Tabla Catering
```
CREATE TABLE Catering(
	Telefono VARCHAR(9),
	Nombre VARCHAR(40),
	ID NUMERIC(5),
	Direccion VARCHAR(40)
	;
)
```

## Tabla menu 
```
CREATE TABLE Menu(
	Nombre VARCHAR(40),
	Tipo VARCHAR(40),
	ID NUMERIC(5)
	;
)
```

## Tabla Platos
```
CREATE TABLE Platos(
	Nombre VARCHAR(40),
	Tipo VARCHAR(40),
	ID NUMERIC(5)
	;
)
```

## Tabla Empleado
```
CREATE TABLE Empleado(
	DNI VARCHAR(5),
	Puesto VARCHAR(20),
	Nombre VARCHAR(50),
	ID NUMERIC(5),
	Fecha_Ing DATE,
	Fecha_nac DATE,
	Salario NUMERIC(5),
	Telefono VARCHAR(9)
	;
)
```

## Tabla Equipo_Tecnico
```
CREATE TABLE Equipo_Tecnico(
	Nombre VARCHAR(20),
	Telefono VARCHAR(9)
	;
)
```

## Tabla Tecnicos
```
CREATE TABLE Tecnicos(
	Nombre VARCHAR(20),
	Telefono VARCHAR(9),
	DNI VARCHAR(9),
	Departemento VARCHAR(20),
	ID NUMERIC(5)
	;
)
```

## Tabla Materiales
```
CREATE TABLE Materiales(
	Categoria VARCHAR(40),
	Precio NUMERIC(10),
	ID NUMERIC(5)
	;
)
``` 

## Tabla Espacios
```
CREATE TABLE Espacios(
	ID NUMERIC(5),
	Dimensiones NUMERIC***Alfanumerico porque lleva m, recordarlo(40),
	Tipo VARCHAR(30),
	Localizacion VARCHAR(50)
	;
)
```

## Tabla Camerinos
```
CREATE TABLE Camerinos(	
	ID NUMERIC(5),
	Inmobiliario VARCHAR(30),
	Capacidad VARCHAR(20)
	;
)
```

## Tabla Escenarios
```
CREATE TABLE Escenarios(
	ID NUMERIC(5),
	Modelo VARCHAR(30),
	Superficie VARCHAR(20)
	;
)
```

## Tabla Artista
```
CREATE TABLE Artista(
	ID NUMERIC(20),
	Nombre VARCHAR(40),
	DNI VARCHAR(9),
	Genero_musical VARCHAR(30)
	;
)
```

## Añadir restricciones

## Tabla Catering
```
ALTER TABLE Catering ADD
PRIMARY KEY (ID);
```

## Tabla Menu 
```
ALTER TABLE Empleados ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Empleados
ADD CONSTRAINT empleados_id_catering FOREIGN KEY (ID_catering) 
    REFERENCES Catering (ID);
```

## Tabla Platos
```
ALTER TABLE Platos ADD 
PRIMARY KEY (ID);
```

## Tabla Empleado
```
ALTER TABLE Empleados ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Empleados
ADD CONSTRAINT empleados_id_catering FOREIGN KEY (ID_catering) 
    REFERENCES Catering (ID);
```

## Tabla Equipo_Tecnico
```
ALTER TABLE Platos ADD 
PRIMARY KEY (ID);
```
```
ALTER TABLE Equipo_Tecnico
ADD CONSTRAINT equipoTecnico_id_catering FOREIGN KEY (ID_catering)
	REFERENCES Catering (ID);
```

## Tabla Tecnicos
```
ALTERT TABLE Tecnicos ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Tecnicos 
ADD CONSTRAINTS tecnicos_nombreEquipoTecnico FOREIGN KEY (nombre_equipotecnico)
	REFERENCES Equipo_Tecnico (nombre);
```

## Tabla Materiales
```
ALTER TABLE Materiales ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Materiales 
ADD CONSTRAINT materiales_nombre_equipoTecnico FOREIGN KEY (nombre_equipoTecnico)
	REFERENCES Equipo_Tecnico (nombre);
```

## Tabla Espacios
```
ALTER TABLE Espacios ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Espacios
ADD CONSTRAINT espacios_nombre_equipoTecnico FOREIGN KEY (nombre_equipoTecnico)
	REFERENCES Equipo_Tecnico (nombre);
```

## Tabla Camerinos
```
ALTER TABLE Camerinos ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Camerinos 
ADD CONSTRAINTS camerinos_IDespacios FOREIGN KEY (ID_espacios)
	REFERENCES Espacios (ID);
```

## Tabla Escenarios
```
ALTER TABLE Escenarios ADD
PRIMARY KEY (ID);
```

```
ALTER TABLE Escenarios 
ADD CONSTRAINTS escenarios_IDespacios FOREIGN KEY (ID_espacios)
	REFERENCES Espacios (ID);

```

## Tabla Artista
```
ALTER TABLE Artista ADD
PRIMARY KEY (ID);
```
```
ALTERT TABLE Artista
ADD CONSTRAINT artistas_idCamerino FOREIGN KEY (ID_Camerino)
	REFERENCES Camerino (ID);

```