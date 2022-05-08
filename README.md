# Operadores-LIKE-y-NOT-LIKE-en-Oracle-SQL
#### son operadores que se utilizan para realizar comparaciones exclusivamente de cadena de textos.
#### el operador like sirve para realizar busqueda pasando como parametros fragmento de textos.

```sql
 create table empleados(
  nombre varchar2(30),
  documento char(8) not null,
  domicilio varchar2(30),
  fechaingreso date,
  seccion varchar2(20),
  sueldo number(6,2),
  primary key(documento)
 );
  insert into empleados
  values('Juan Perez','22333444','Colon 123',to_date('08/10/1990','dd/mm/yyyy'),'Gerencia',900.50);
 insert into empleados
  values('Ana Acosta','23444555','Caseros 987',to_date('18/12/1995','dd/mm/yyyy'),'Secretaria',590.30);
 insert into empleados
  values('Lucas Duarte','25666777','Sucre 235',to_date('15/05/2005','dd/mm/yyyy'),'Sistemas',790);
 insert into empleados
  values('Pamela Gonzalez','26777888','Sarmiento 873',to_date('12/02/1999','dd/mm/yyyy'),'Secretaria',550);
 insert into empleados
  values('Marcos Juarez','30000111','Rivadavia 801',to_date('22/09/2002','dd/mm/yyyy'),'Contaduria',630.70);
 insert into empleados
  values('Yolanda perez','35111222','Colon 180',to_date('08/10/1990','dd/mm/yyyy'),'Administracion',400);
 insert into empleados
  values('Rodolfo perez','35555888','Coronel Olmedo 588',to_date('28/05/1990','dd/mm/yyyy'),'Sistemas',800);
  
  ```
  
    >select * from empleados

 | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Juan Perez | 22333444 |  Colon 123   | 08/10/1990  | Gerencia | 900.50|
 | Ana Acosta | 23444555 |  Caseros 987   | 18/12/1995  | Secretaria | 590.30|
 | Lucas Duarte | 25666777|  Sucre 235   | 15/05/2005  | Sistemas | 790|
 | Pamela Gonzalez | 26777888 |  Sarmiento 873   | 12/02/1999  | Secretaria | 550| 
 | Marcos Juarez | 30000111 |  Rivadavia 801   | 22/09/2002  | Contaduria | 630.70| 
 | Yolanda perez | 35111222 |  Colon 180   | 08/10/1990  | Administracion | 400|
 | Rodolfo perez | 35555888 |  Coronel Olmedo 588  | 28/05/1990  | Sistemas | 800| 
 
 
___
```sql
select * from empleados where nombre like '%Perez%';
-- el operador like busca que coincida cada una de las letras que pasamos como parametros, es por eso que losa pellidos con minuscula no se muestran.
 ```
 
 | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Juan Perez | 22333444 |  Colon 123   | 08/10/1990  | Gerencia | 900.50|
 
 
 ___
```sql
select * from empleados where nombre like '%erez%';
```
 | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Juan Perez | 22333444 |  Colon 123   | 08/10/1990  | Gerencia | 900.50|
 | Yolanda perez | 35111222 |  Colon 180   | 08/10/1990  | Administracion | 400|
 | Rodolfo perez | 35555888 |  Coronel Olmedo 588  | 28/05/1990  | Sistemas | 800| 
 
 
 ```sql
 select * from empleados where nombre not like '%Perez%';
 -- el operador not like excluye el apellido Perez con mayusuca
 ```
  | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Ana Acosta | 23444555 |  Caseros 987   | 18/12/1995  | Secretaria | 590.30|
 | Lucas Duarte | 25666777|  Sucre 235   | 15/05/2005  | Sistemas | 790|
 | Pamela Gonzalez | 26777888 |  Sarmiento 873   | 12/02/1999  | Secretaria | 550| 
 | Marcos Juarez | 30000111 |  Rivadavia 801   | 22/09/2002  | Contaduria | 630.70| 
 | Yolanda perez | 35111222 |  Colon 180   | 08/10/1990  | Administracion | 400|
 | Rodolfo perez | 35555888 |  Coronel Olmedo 588  | 28/05/1990  | Sistemas | 800| 
 
 ___
 
 ```sql
 select * from empleados where documento like '35%';
 --si colocamos el % al final nos va traer todo los valores q coincidan al principio en este caso 35.
```

 | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Yolanda perez | 35111222 |  Colon 180   | 08/10/1990  | Administracion | 400|
 | Rodolfo perez | 35555888 |  Coronel Olmedo 588  | 28/05/1990  | Sistemas | 800| 

____

 ```sql
 select * from empleados where documento like '%888';
 --si colocamos el % al inicio va buscar trodo los valores q finalicen con 888.
```
  | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Pamela Gonzalez | 26777888 |  Sarmiento 873   | 12/02/1999  | Secretaria | 550| 
 | Rodolfo perez | 35555888 |  Coronel Olmedo 588  | 28/05/1990  | Sistemas | 800| 
 
 
 ___
 ```sql
 select * from empleados where domicilio like 'Co%8%';
 ```
 | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Yolanda perez | 35111222 |  Colon 180   | 08/10/1990  | Administracion | 400|
 | Rodolfo perez | 35555888 |  Coronel Olmedo 588  | 28/05/1990  | Sistemas | 800| 
 
 ___
 
```sql
select * from empleados where seccion like 'G_______';
los subgiones debe de coincidir en la cantidad de letras como guiones tiene la consulta
```
 | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Juan Perez | 22333444 |  Colon 123   | 08/10/1990  | Gerencia | 900.50|
 
 
 ___
 ```sql
 select * from empleados where sueldo like '%5__%';
-- trae los sueldos q contenga un 5 y dos valores enteros
 ```
 | nombre            | documento           |   domicilio   |  fechaingreso   |  seccion   |  sueldo  |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:|
 | Ana Acosta | 23444555 |  Caseros 987   | 18/12/1995  | Secretaria | 590.30|
 | Pamela Gonzalez | 26777888 |  Sarmiento 873   | 12/02/1999  | Secretaria | 550| 
