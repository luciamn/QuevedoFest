# CREACION DE TABLAS Y OTROS OBJETOS

## Creacion de Tablas

## Tabla Catering
```
CREATE TABLE Catering(
	Telefono VARCHAR(9),
	Nombre VARCHAR(40),
	ID NUMERIC(5),
	Direccion VARCHAR(40)
)
;
```

## Tabla menu 
```
CREATE TABLE Menu(
	Nombre VARCHAR(40),
	Tipo VARCHAR(40),
	ID NUMERIC(5),
	ID_catering INTEGER NOT NULL
)
;
```

## Tabla Platos
```
CREATE TABLE Platos(
	Nombre VARCHAR(40),
	Tipo VARCHAR(40),
	ID NUMERIC(5)
)
;
```

## Tabla Empleado
```
CREATE TABLE Empleado(
	Puesto VARCHAR(20),
	Nombre VARCHAR(50),
	ID NUMERIC(5),
	Fecha_nac DATE,
	Fecha_Ing DATE,
	Salario NUMERIC(5),
	Telefono VARCHAR(9),
	ID_catering INTEGER NOT NULL,
	DNI VARCHAR(9)
)
;
```

## Tabla Equipo_Tecnico
```
CREATE TABLE Equipo_Tecnico(
	Nombre VARCHAR(20),
	Telefono VARCHAR(9),
	ID NNUMERIC(5),
	ID_catering INTEGER NOT NULL
)
;
```

## Tabla Tecnico
```
CREATE TABLE Tecnico(
	Nombre VARCHAR(50),
	Telefono VARCHAR(9),
	DNI VARCHAR(9),
	Departemento VARCHAR(20),
	ID NUMERIC(5),
	nombre_equipotecnico VARCHAR(30)
)
;
```

## Tabla Materiales
```
CREATE TABLE Materiales(
	Categoria VARCHAR(40),
	Precio NUMERIC(10),
	ID NUMERIC(5),
	nombre_equipotecnico VARCHAR(30)
)
;
``` 

## Tabla Espacios
```
CREATE TABLE Espacio(
	ID NUMERIC(5),
	Dimensiones VARCHAR(40),
	Tipo VARCHAR(30),
	Localizacion VARCHAR(50),
	nombre_equipotecnico VARCHAR(30)
)
;
```

## Tabla Camerinos
```
CREATE TABLE Camerino(	
	ID NUMERIC(5),
	Inmobiliario VARCHAR(30),
	Capacidad VARCHAR(20),
	ID_espacio INTEGER NOT NULL
)
;
```

## Tabla Escenarios
```
CREATE TABLE Escenario(
	ID NUMERIC(5),
	Modelo VARCHAR(30),
	Superficie VARCHAR(20),
	ID_espacio INTEGER NOT NULL
)
;
```

## Tabla Artista
```
CREATE TABLE Artista(
	ID NUMERIC(20),
	Nombre VARCHAR(40),
	DNI VARCHAR(9),
	Genero_musical VARCHAR(30),
	ID_camerino INTEGER NOT NULL
)
;
```

## Añadir restricciones

## Tabla Catering
```
ALTER TABLE Catering ADD
PRIMARY KEY (ID);
```

## Tabla Menu 
```
ALTER TABLE Menu ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Menu
ADD CONSTRAINT menu_id_catering FOREIGN KEY (ID_catering) 
    REFERENCES Catering (ID);
```

## Tabla Platos
```
ALTER TABLE Platos ADD 
PRIMARY KEY (ID);
```

## Tabla Empleado
```
ALTER TABLE Empleado ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Empleado
ADD CONSTRAINT empleados_id_catering FOREIGN KEY (ID_catering) 
    REFERENCES Catering (ID);
```

## Tabla Equipo_Tecnico
```
ALTER TABLE equipo_tecnico ADD 
PRIMARY KEY (nombre);
```
```
ALTER TABLE Equipo_Tecnico
ADD CONSTRAINT equipoTecnico_id_catering FOREIGN KEY (ID_catering)
	REFERENCES Catering (ID);
```

## Tabla Tecnicos
```
ALTER TABLE Tecnico ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Tecnico 
ADD CONSTRAINT tecnico_nombreEquipotecnico FOREIGN KEY (nombre_equipotecnico)
	REFERENCES Equipo_Tecnico (nombre);
```

## Tabla Materiales
```
ALTER TABLE Materiales ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Materiales 
ADD CONSTRAINT materiales_nombre_equipoTecnico FOREIGN KEY (nombre_equipotecnico)
	REFERENCES Equipo_Tecnico (nombre);
```

## Tabla Espacios
```
ALTER TABLE Espacio ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Espacio
ADD CONSTRAINT espacios_nombre_equipoTecnico FOREIGN KEY (nombre_equipotecnico)
	REFERENCES Equipo_Tecnico (nombre);
```

## Tabla Camerinos
```
ALTER TABLE Camerino ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Camerino 
ADD CONSTRAINT camerinos_IDespacios FOREIGN KEY (ID_espacio)
	REFERENCES Espacio (ID);
```

## Tabla Escenarios
```
ALTER TABLE Escenario ADD
PRIMARY KEY (ID);
```

```
ALTER TABLE Escenario 
ADD CONSTRAINT escenarios_IDespacios FOREIGN KEY (ID_espacio)
	REFERENCES Espacio (ID);

```

## Tabla Artista
```
ALTER TABLE Artista ADD
PRIMARY KEY (ID);
```
```
ALTER TABLE Artista
ADD CONSTRAINT artistas_idCamerino FOREIGN KEY (ID_camerino)
	REFERENCES Camerino (ID);

```