# Modelo Relacional


Catering(ID(PK), nombre, dirección, teléfono)

Empleados(DNI, puesto, nombre, (ID(PK)), fehca_nac, salario, fecha_ing, teléfono, ID_catering(FK))

Menu(ID(PK), tipo, ID_catering(FK))

Platos(ID(PK), tipo, nombre)

Menu_Platos(ID_plato(PK), ID_menu(PK))

Equipo_Tecnico(nombre(PK), departamento, ID_catering(FK))

Materiales(ID(PK), precio, categoria, nombre_equipoTecnico(FK))

Espacios(ID(PK) ,Dimensiones, tipo, Localizacion, nombre_equipoTecnico(FK))

Camerinos (ID(PK), Inmboliario, Capacidad, ID_espacio(FK))

Artista(ID(PK), DNI, nombre, genero_musical ID_camerino(FK))

Escenarios(ID(PK), modelo, superficie, ID_espacio(FK))

Tecnicos(Nombre, telefono, DNI, departamento, ID(PK), nombre_equipoTecnico(FK))

Escenarios_Artistas(ID_Escenarios(PK), ID_Artistas(PK))

