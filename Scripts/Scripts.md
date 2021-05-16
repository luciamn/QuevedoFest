## Script 1
Un script que muestre el numero de platos que gestiona el catering 
```sql
do
$$
declare
v_num_platos integer := 0;
begin
	select count(*)
	into v_num_platos
	from platos;
raise notice 'El numero de platos es %', v_num_platos;
end;
$$
```

## Script 2
Un script que muestre el precio del Microfono Mark SH, cuyo id es 9
```sql
do
$$
declare
v_precio materiales.precio%type;
begin
	select precio
	into v_precio 
	from materiales
	where id = 9;
raise notice 'El precio del microfono es %', v_precio;
end;
$$
```

## Script 3
Un script que muestre el puesto del empleado Andres Barbera
```sql
do
$$
declare
v_puesto empleado.puesto%type;
begin
	select puesto
	into v_puesto 
	from empleado
	where id = 38;
raise notice 'El puesto de Andres es %', v_puesto;
end;
$$
```

## Script 4
Mostrar los 5 materiales mas caros con un loop
```sql
$$
declare
v_ej record;
begin
	for v_ej in select nombre, precio
		from materiales
		limit 5
	loop
		raise notice 'Material: %, Precio: % euros',
			v_ej.nombre,
			v_ej.precio;
	end loop;
end;
$$
```

## Scrip 5
Mostrar el nombre de un cliente dado su id, si no se encuenta mostrar un mensaje	
```sql
do 
$$
declare
v_registro record;
v_art_id int := 70;
begin
	select id, nombre
	into strict v_registro
	from artista
	where id = v_art_id;

	exception
	when no_data_found then
	raise exception 'Empleado % no encontrado', v_art_id;
	when others then 
	raise exception 'Error inesperado';
end;
$$
```
Resultado:
```
SQL Error [P0001]: ERROR: Empleado 70 no encontrado
  Where: PL/pgSQL function inline_code_block line 13 at RAISE
```

## Script 6
Realizaremos la misma consulta que el script 5, pero introduciremos la variable found, donde si el id es correcto nos devolvera el artista, pero si nos devolvera un false
```sql
do 
$$
declare
v_artista artista%rowtype;
v_art_id artista.id%type = 4001;
begin
	select * from artista
	into  v_artista
	where id = v_art_id;

	if not found then 
		raise notice 'Empleado % no encontrado', v_art_id;
	else
		raise notice 'Nombre del artista', v_artista.nombre;
	end if;
end;
$$
```