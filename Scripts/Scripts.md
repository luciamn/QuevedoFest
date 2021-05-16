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

